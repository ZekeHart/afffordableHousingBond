<!--

Links:
  Events: https://vuejs.org/v2/guide/events.html
  Computed properties: https://vuejs.org/v2/guide/computed.html

Data:
  http://www.nconemap.com//

-->
<template>
<div class="mainContainer">
  <Scrollama @step-enter="stepEnterHandler">
      <div class='mapImg'  slot='graphic'>
        <div class='holder'>
          <!-- <strong>Percent Change in White Population 2000-2016</strong> -->
          <div class="row">
            <div class="col-9">
              <div class='mapHolder'>
                <durham-map v-bind:propval='pushSelect'
                v-bind:scrollVal='scrollVal'
                  v-on:durhamtrSelected='onDurhamtrSelected'
                  v-on:durhamtrDeselected='onDurhamtrDeselected'
                />
              </div>
            </div>
            <div class="col-3">
              <tooltip v-if='currentDurhamtr'
                v-bind:title='currentDurhamtrTitle'
                v-bind:description='currentDurhamtrDescription'
              />
            </div>
          </div>
      </div>
    </div>
        <div class='step textContainer'  data-step-no="pcpop0016">
          <h3 id='lorem-title' class='title'>Percent Change in Population between 2000-2016</h3>

          <p class='text'>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquid cumque non quaerat vitae animi? Assumenda nostrum alias corporis fugiat facilis vero ducimus, beatae aliquam, in perferendis, consectetur saepe unde velit. Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquid cumque non quaerat vitae animi? Assumenda nostrum alias corporis fugiat facilis vero ducimus, beatae aliquam, in perferendis, consectetur saepe unde velit.</p>
      </div>

      <div class='step textContainer' data-step-no="pcnhwht0016">
          <h3 class='title'>Percent Change in White Population between 2000-2016</h3>

          <p class='text'>Fixie dirty durham consensus big green wall beaver queen sustainable urban ministries dapper, broad street wool e bull old north innovation bowtie maker, southsquare historic preservation maker full frame sodu the buehler. The bulls hipster blues major sodu duke chapel dino trail eagles, major the state of things ninth street miami boulevard diy. Durham goldenbelt duke park local erwin road saint joseph's, start-up adf miami boulevard bulltown strutters ccb plaza french press, erwin terrace the double nickel merge records elf. Angier drive medicine dance the indy one forty seven train arm wrestling, duke chapel university science and math partner erwin square black wall street major, seventy french press dance dur'm 15-501. Blue devils bouncing bulldogs third fridays the double nickel chapel drive beer doughman seventy west village wunc, northeast central luewwd hipster hub coworking erwin square authentic innovation. Seeds the buehler oprah building walltown arm wrestling historic preservation local, blackwell urban ministries old north the kress historic preservation doughman, trinity park foodie bay 7 eno river bragtown.</p>
      </div>
      <div class='step textContainer' data-step-no="pcnhblk0016">
          <h3 id='lorem-title' class='title'>Percent Change in Black Population between 2000-2016</h3>

          <p class='text'>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquid cumque non quaerat vitae animi? Assumenda nostrum alias corporis fugiat facilis vero ducimus, beatae aliquam, in perferendis, consectetur saepe unde velit. Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquid cumque non quaerat vitae animi? Assumenda nostrum alias corporis fugiat facilis vero ducimus, beatae aliquam, in perferendis, consectetur saepe unde velit.</p>
      </div>

      <div class='step textContainer' id='home' data-step-no="pcmhmval0016a17">
          <h3 class='title'>Percent change in Median Home Value, 2000-2016 in 2017 dollars</h3>

          <p class='text'>Fixie dirty durham consensus big green wall beaver queen sustainable urban ministries dapper, broad street wool e bull old north innovation bowtie maker, southsquare historic preservation maker full frame sodu the buehler. The bulls hipster blues major sodu duke chapel dino trail eagles, major the state of things ninth street miami boulevard diy. Durham goldenbelt duke park local erwin road saint joseph's, start-up adf miami boulevard bulltown strutters ccb plaza french press, erwin terrace the double nickel merge records elf. Angier drive medicine dance the indy one forty seven train arm wrestling, duke chapel university science and math partner erwin square black wall street major, seventy french press dance dur'm 15-501. Blue devils bouncing bulldogs third fridays the double nickel chapel drive beer doughman seventy west village wunc, northeast central luewwd hipster hub coworking erwin square authentic innovation. Seeds the buehler oprah building walltown arm wrestling historic preservation local, blackwell urban ministries old north the kress historic preservation doughman, trinity park foodie bay 7 eno river bragtown.</p>
      </div>
      <div class='step textContainer' id='' data-step-no="pcmrent0016a17">
          <h3 class='title'>Percent Change in Median Contract Rent between 2000 and 2016, Adjusted to 2017 Dollars</h3>

          <p class='text'>Fixie dirty durham consensus big green wall beaver queen sustainable urban ministries dapper, broad street wool e bull old north innovation bowtie maker, southsquare historic preservation maker full frame sodu the buehler. The bulls hipster blues major sodu duke chapel dino trail eagles, major the state of things ninth street miami boulevard diy. Durham goldenbelt duke park local erwin road saint joseph's, start-up adf miami boulevard bulltown strutters ccb plaza french press, erwin terrace the double nickel merge records elf. Angier drive medicine dance the indy one forty seven train arm wrestling, duke chapel university science and math partner erwin square black wall street major, seventy french press dance dur'm 15-501. Blue devils bouncing bulldogs third fridays the double nickel chapel drive beer doughman seventy west village wunc, northeast central luewwd hipster hub coworking erwin square authentic innovation. Seeds the buehler oprah building walltown arm wrestling historic preservation local, blackwell urban ministries old north the kress historic preservation doughman, trinity park foodie bay 7 eno river bragtown.</p>
      </div>
      <div class='step textContainer' id='' data-step-no="grprchi16">
          <h3 class='title'>Gross Rent as Percent of Household Income in 2016</h3>

          <p class='text'>Fixie dirty durham consensus big green wall beaver queen sustainable urban ministries dapper, broad street wool e bull old north innovation bowtie maker, southsquare historic preservation maker full frame sodu the buehler. The bulls hipster blues major sodu duke chapel dino trail eagles, major the state of things ninth street miami boulevard diy. Durham goldenbelt duke park local erwin road saint joseph's, start-up adf miami boulevard bulltown strutters ccb plaza french press, erwin terrace the double nickel merge records elf. Angier drive medicine dance the indy one forty seven train arm wrestling, duke chapel university science and math partner erwin square black wall street major, seventy french press dance dur'm 15-501. Blue devils bouncing bulldogs third fridays the double nickel chapel drive beer doughman seventy west village wunc, northeast central luewwd hipster hub coworking erwin square authentic innovation. Seeds the buehler oprah building walltown arm wrestling historic preservation local, blackwell urban ministries old north the kress historic preservation doughman, trinity park foodie bay 7 eno river bragtown.</p>
      </div>
      <div class='step textContainer' id='' data-step-no="mmocphi16">
          <h3 class='title'>Morgage Monthly Owners Cost as a Percent of Household Income in 2016</h3>

          <p class='text'>Fixie dirty durham consensus big green wall beaver queen sustainable urban ministries dapper, broad street wool e bull old north innovation bowtie maker, southsquare historic preservation maker full frame sodu the buehler. The bulls hipster blues major sodu duke chapel dino trail eagles, major the state of things ninth street miami boulevard diy. Durham goldenbelt duke park local erwin road saint joseph's, start-up adf miami boulevard bulltown strutters ccb plaza french press, erwin terrace the double nickel merge records elf. Angier drive medicine dance the indy one forty seven train arm wrestling, duke chapel university science and math partner erwin square black wall street major, seventy french press dance dur'm 15-501. Blue devils bouncing bulldogs third fridays the double nickel chapel drive beer doughman seventy west village wunc, northeast central luewwd hipster hub coworking erwin square authentic innovation. Seeds the buehler oprah building walltown arm wrestling historic preservation local, blackwell urban ministries old north the kress historic preservation doughman, trinity park foodie bay 7 eno river bragtown.</p>
      </div>
      <div class='step textContainer' id='' data-step-no="hinc16">
          <h3 class='title'>Median Household Income in 2016</h3>

          <p class='text'>Fixie dirty durham consensus big green wall beaver queen sustainable urban ministries dapper, broad street wool e bull old north innovation bowtie maker, southsquare historic preservation maker full frame sodu the buehler. The bulls hipster blues major sodu duke chapel dino trail eagles, major the state of things ninth street miami boulevard diy. Durham goldenbelt duke park local erwin road saint joseph's, start-up adf miami boulevard bulltown strutters ccb plaza french press, erwin terrace the double nickel merge records elf. Angier drive medicine dance the indy one forty seven train arm wrestling, duke chapel university science and math partner erwin square black wall street major, seventy french press dance dur'm 15-501. Blue devils bouncing bulldogs third fridays the double nickel chapel drive beer doughman seventy west village wunc, northeast central luewwd hipster hub coworking erwin square authentic innovation. Seeds the buehler oprah building walltown arm wrestling historic preservation local, blackwell urban ministries old north the kress historic preservation doughman, trinity park foodie bay 7 eno river bragtown.</p>
      </div>
      <div class='step textContainer' id='' data-step-no="hincw16">
          <h3 class='title'>Median Household Income for White Residents in 2016</h3>

          <p class='text'>Fixie dirty durham consensus big green wall beaver queen sustainable urban ministries dapper, broad street wool e bull old north innovation bowtie maker, southsquare historic preservation maker full frame sodu the buehler. The bulls hipster blues major sodu duke chapel dino trail eagles, major the state of things ninth street miami boulevard diy. Durham goldenbelt duke park local erwin road saint joseph's, start-up adf miami boulevard bulltown strutters ccb plaza french press, erwin terrace the double nickel merge records elf. Angier drive medicine dance the indy one forty seven train arm wrestling, duke chapel university science and math partner erwin square black wall street major, seventy french press dance dur'm 15-501. Blue devils bouncing bulldogs third fridays the double nickel chapel drive beer doughman seventy west village wunc, northeast central luewwd hipster hub coworking erwin square authentic innovation. Seeds the buehler oprah building walltown arm wrestling historic preservation local, blackwell urban ministries old north the kress historic preservation doughman, trinity park foodie bay 7 eno river bragtown.</p>
      </div>
      <div class='step textContainer' id='' data-step-no="hincb16">
          <h3 class='title'>Median Household Income for Black Residents in 2016</h3>

          <p class='text'>Fixie dirty durham consensus big green wall beaver queen sustainable urban ministries dapper, broad street wool e bull old north innovation bowtie maker, southsquare historic preservation maker full frame sodu the buehler. The bulls hipster blues major sodu duke chapel dino trail eagles, major the state of things ninth street miami boulevard diy. Durham goldenbelt duke park local erwin road saint joseph's, start-up adf miami boulevard bulltown strutters ccb plaza french press, erwin terrace the double nickel merge records elf. Angier drive medicine dance the indy one forty seven train arm wrestling, duke chapel university science and math partner erwin square black wall street major, seventy french press dance dur'm 15-501. Blue devils bouncing bulldogs third fridays the double nickel chapel drive beer doughman seventy west village wunc, northeast central luewwd hipster hub coworking erwin square authentic innovation. Seeds the buehler oprah building walltown arm wrestling historic preservation local, blackwell urban ministries old north the kress historic preservation doughman, trinity park foodie bay 7 eno river bragtown.</p>
      </div>
    </Scrollama>
    </div>
</template>

<script>
function load (component) {
  return () => import(`src/${component}.vue`)
}

import { routes } from 'router/graphs'
import setOptions from './ltdbacs_trts_vuevarmenuoptions'
import { groupOptions } from './ltdbacs_trts_vuegroupoptions'
import popupValues from './ltdbacs_trts_vuemappopup'
import 'intersection-observer'
import Scrollama from 'vue-scrollama'

// d3 and map stuff
const d3 = require('d3')
const map = load('components/graphs/durhamtrts-map/mapcartogram')
const tooltip = load('mixins/tooltip')

// Data stuff
// const LTDBACS_DATA_PATH = 'http://127.0.0.1:8000/api/ltdbacs_trts_7016/?format=json'
const LTDBACS_DATA_PATH = 'statics/data/ltdbacs7016tr.json'
var _ = require('lodash')

import {
  QLayout
} from 'quasar'

export default {
  components: {
    durhamMap: map,
    tooltip: tooltip,
    QLayout,
    Scrollama
  },
  created: function () {
    var that = this

    this.durhamtrtsData = {}

    d3.json(LTDBACS_DATA_PATH, function (data) {
      data.map(function (d) {
        that.vardata = d[that.selectvariable.value]
        d.value = +that.vardata
        that.durhamtrtsData[d.id] = d
        return d
      })
    })
  },
  data: function () {
    return {
      items: routes,
      durhamtrtsData: undefined,
      vardata: undefined,
      currentDurhamtr: undefined,
      groupOptions: groupOptions,
      selectgroup: {label: 'Durhams Demographic Numbers', value: 'democount'},
      selectvariable: {label: 'Total Population in 1970', value: 'pop70'},
      pushSelect: _.take(this.selectvariable),
      currStep: null,
      testButton: 'initial',
      scrollVal: 0
    }
  },
  computed: {
    varOptions: setOptions,
    currentDurhamtrDescription: popupValues,
    currentDurhamtrTitle: function () {
      return 'GEOID: ' + this.currentDurhamtr.id
    }
  },
  methods: {
    onDurhamtrSelected: function (durhamtrGeoID) {
      this.currentDurhamtr = this.durhamtrtsData[durhamtrGeoID]
    },
    onDurhamtrDeselected: function (durhamtrGeoID) {
      this.currentDurhamtr = undefined
    },
    newVar: function () {
      if (this.pushSelect.length === 0) {
        this.pushSelect.push(this.selectvariable)
      }
      else if (this.pushSelect.length === 1) {
        this.pushSelect.splice(0, 1)
        this.pushSelect.push(this.selectvariable)
      }
    },
    changeJoey: function () {
      this.testButton = 'pop70'
    },
    stepEnterHandler ({element, index, direction}) {
      // handle the step-event as required here
      this.scrollVal = element.dataset.stepNo
    }
  }
}
</script>
<style src="vue-scrollama/dist/vue-scrollama.css" >
</style>

<style lang="stylus" scoped>

@media (min-width: 500px) {
  .holder {
    position: relative;
    padding-top: 10px;
    height: 700px;
    width: 580px;
    margin: auto;
  }
}
@media (max-width: 499px) {
  .holder {
    position: relative;
    padding-top: 40px;
    height: 700px;
    width: 580px;
    margin: auto;
  }
}
.mapHolder {
  position: absolute;
  margin: auto;
}
@media (min-width: 600px) {
  .select-group {
    width: 500px;
    bottom: 60px;
  }
  .select-variable {
    width: 500px;
    bottom: 60px;
    overflow:hidden; 
    white-space:pre;
    word-wrap: normal !important;
    white-space: normal;
    text-overflow:ellipsis;
    -webkit-appearance: none;
  }
}
@media (max-width: 599px) {
  .select-group {
    width: 300px;
    bottom: 60px;
    overflow:hidden; 
    white-space:pre;
    word-wrap: normal !important;
    white-space: normal;
    text-overflow:ellipsis;
    -webkit-appearance: none;
  }
  .select-variable {
    width: 300px;
    bottom: 60px;
    overflow:hidden; 
    white-space:pre;
    word-wrap: normal !important;
    white-space: normal;
    text-overflow:ellipsis;
    -webkit-appearance: none;
  }
}
.flex-col-docs
  .doc-container
    padding 15px
  .column > div
    padding 10px 15px
    background rgba(86, 61, 124, .15)
    border 1px solid rgba(86, 61, 124, .2)
  .column + .column
    margin-top 1rem
  .nesting-example
    .column + .column
      margin 0
  .minheight-column .column
    min-width 5rem
  .with-bg .column
    background rgba(255, 0, 0, .1)
</style>
