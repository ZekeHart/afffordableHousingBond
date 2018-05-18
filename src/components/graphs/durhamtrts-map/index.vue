<!--

Links:
  Events: https://vuejs.org/v2/guide/events.html
  Computed properties: https://vuejs.org/v2/guide/computed.html

Data:
  http://www.nconemap.com//

-->
<template>
  <q-layout
    ref="layout"
    view="lHh Lpr fff"
    v-bind:left-class="{'bg-grey-2': true}"
  >
    <h6><center>{{ $route.name }}</center></h6>

    <div class='holder'>
      <div class='mapHolder'>
        <durham-map v-bind:propval='pushSelect'
          v-on:durhamtrSelected='onDurhamtrSelected'
          v-on:durhamtrDeselected='onDurhamtrDeselected'
        />
      </div>
      <tooltip
        v-if='currentDurhamtr'
        v-bind:title='currentDurhamtrTitle'
        v-bind:description='currentDurhamtrDescription'
      />
      <center>
      <q-select 
        separator
        v-model='select.value'
        v-bind:options=setOptions
        v-on:input='newProp'
      />
      </center>
    </div>
  </q-layout>
</template>

<script>
function load (component) {
  return () => import(`src/${component}.vue`)
}

/* function numberWithCommas (x) {
  return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
} */

import { routes } from 'router/graphs'
import { options as selectOptions } from './ltdbacs_trts_vuemapmenu'
/* import setOptions from './ltdbacs_trts_vuevaroptions'
import { groupOptions } from './ltdbacs_trts_vuegroupoptions' */
import popupValues from './ltdbacs_trts_vuemappopup'

// d3 and map stuff
const d3 = require('d3')
const map = load('components/graphs/durhamtrts-map/mapcartogram')

// Menu and tooltip stuff
import {
  QSelect,
  QLayout
} from 'quasar'

const tooltip = load('mixins/tooltip')

// Data stuff
const LTDBACS_DATA_PATH = 'http://127.0.0.1:8000/api/ltdbacs_trts_7016/?format=json'
var _ = require('lodash')

export default {
  components: {
    durhamMap: map,
    tooltip: tooltip,
    QSelect,
    QLayout
  },
  created: function () {
    var that = this

    this.durhamtrtsData = {}

    d3.json(LTDBACS_DATA_PATH, function (data) {
      data.map(function (d) {
        that.propdata = d[that.select.value]
        // .split(',').join('')
        d.value = +that.propdata
        that.durhamtrtsData[d.id] = d
        return d
      })
    })
  },
  data: function () {
    return {
      items: routes,
      durhamtrtsData: undefined,
      propdata: undefined,
      currentDurhamtr: undefined,
      select: {label: 'Total Population in 1970', value: 'pop70', type: 'trts'},
      setOptions: selectOptions,
      pushSelect: _.take(this.select)
    }
  },
  computed: {
    currentDurhamtrDescription: popupValues,
    currentDurhamtrTitle: function () {
      if (this.select.type === 'trts') {
        return 'GEOID: ' + this.currentDurhamtr.id
      }
    }
  },
  methods: {
    onDurhamtrSelected: function (durhamtrGeoID) {
      this.currentDurhamtr = this.durhamtrtsData[durhamtrGeoID]
    },
    onDurhamtrDeselected: function (durhamtrGeoID) {
      this.currentDurhamtr = undefined
    },
    newProp: function () {
      if (this.pushSelect.length === 0) {
        this.pushSelect.push(this.select)
      }
      else if (this.pushSelect.length === 1) {
        this.pushSelect.splice(0, 1)
        this.pushSelect.push(this.select)
      }
    }
  }
}
</script>

<style scoped>
.holder {
  position: relative;
  padding-top: 50px;
  height: 700px;
  width: 580px;
  margin: auto;
}
.mapHolder {
  position: absolute;
  margin: auto;
}
@media (min-width: 600px) {
  .q-select {
    width: 500px;
    bottom: 60px;
  }
}
@media (max-width: 599px) {
  .q-select {
    width: 300px;
    bottom: 60px;
  }
}
</style>