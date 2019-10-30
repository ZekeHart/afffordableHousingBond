<!--

Links:
  Events: https://vuejs.org/v2/guide/events.html
  Computed properties: https://vuejs.org/v2/guide/computed.html

Data:
  http://www.nconemap.com//

-->
<template>
<div class="mainContainer">
  <mq-layout mq="tablet+">
    <Scrollama :debug="false"
        :offset="0.6" 
        @step-enter="stepEnterHandler">
        <div class='mapImg'  slot='graphic'>
          <div class='holder'>
            <!-- <strong>Percent Change in White Population 2000-2016</strong> -->
            <div class="row">
              <div class="col-9">
                <div class='mapHolder'>
                  <durham-map 
                    v-bind:scrollVal='scrollVal' initValue='pcpop0016'
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
      <div class='step textContainer' id='home' data-step-no="grprchi16">
            <h2 class="categoryTitle">Housing Cost Changes</h2>
            <p class='subtitle'>Regardless of where you look in the city, renters pay a large share of their incomes on housing costs. In fact, almost half of all households in the Raleigh-Durham region spent 30% or more of their monthly income on rent or mortgage payments.</p>
            <h3 class='title'>Gross Rent as Percent of Household Income in 2016 (Click to zoom in)</h3>
        </div>
        <div class='step textContainer' id='' data-step-no="mmocphi16">
            
            <p class='subtitle'>Although owners are less cost burdened than renters, many homeowners still pay 30% or more of their monthly incomes on housing costs.</p>
            <h3 class='title'>Morgage Monthly Owners Cost as a Percent of Household Income in 2016 (Click to zoom in)</h3>
        </div>
        <div id='' class='step textContainer' data-step-no="pcmhmval0016a17">

            <p class='subtitle'>As downtown Durham has become more popular as a place to live, work, and play, housing values have increased in the central areas of the city, while prices have dropped in farther-afield suburban parts of the city. The areas closest to the border of the county have seen increases in median home value, perhaps due to construction of large, expensive homes on large, suburban tracts.</p>
            <h3 class='title'>Percent change in Median Home Value, 2000-2016 in 2017 dollars (Click to zoom in)</h3>
        </div>
        <div class='step textContainer' id='' data-step-no="pcmrent0016a17">

            <p class='subtitle'>We see a similar relationship in this map as with the changes in median home value, although both the increases and decreases in rent seem more dramatic than the changes in home values. The central and downtown areas of the city have seen high rent growth while the close-in suburban areas have seen rents drop. Just as home values increase on the outskirts of the county, so, too, have these areas experienced significant rent increases, perhaps caused by dramatic growth in Durham’s population.</p>
            <h3 class='title'>Percent Change in Median Contract Rent between 2000 and 2016, Adjusted to 2017 Dollars</h3>
        </div>
          <div id='population' class='step textContainer'  data-step-no="pcpop0016">
              <h2 class="categoryTitle">Population Changes</h2>

              <p class='subtitle'>Most areas of the city have seen dramatic population growth, one of the factors in rent growth. But this picture changes depending on how you filter the data, especially when considering race.</p>
              <h3 class='title'>Percent Change in Population between 2000-2016 (Click to zoom in)</h3>
        </div>

        <div class='step textContainer' data-step-no="pcnhwht0016">

            <p class='subtitle'>With some exceptions, the majority of population growth among white residents has occurred in the central parts of the city. The more suburban portions of the city have seen decreases in the white population since 2000.</p>
            <h3 class='title'>Percent Change in White Population between 2000-2016 (Click to zoom in)</h3>
        </div>
        <div class='step textContainer' data-step-no="pcnhblk0016">

            <p class='subtitle'>This map is almost the exact inverse of the previous one, suggesting that African-American residents have been leaving and/or displaced from the central areas of Durham and relocating in the more suburban areas of the city.</p>
            <h3 id='lorem-title' class='title'>Percent Change in African-American Population between 2000-2016 (Click to zoom in)</h3>
        </div>

        <div id='income' class='step textContainer' data-step-no="pchinc0016a17">
            <h2 class="categoryTitle">Income Changes</h2>

            <p class='subtitle'>Another factor that impacts the affordability of housing is income. This map demonstrates that the central parts and most suburban areas of the city have seen income increases, while everything in between has seen stagnant or decreasing incomes.</p>
            <h3 class='title'>Percent Change in Household Income between 2000 and 2016, Adjusted to 2017 Dollars (Click to zoom in)</h3>
        </div>
        <div class='step textContainer' id='' data-step-no="pchincw0016a17">

            <p class='subtitle'>Combined with the population map, this shows that not only did white residents move to more central parts of Durham but their incomes also rose very rapidly, too.</p>
            <h3 class='title'>Percent Change in Household Income for White Population between 2000 and 2016, Adjusted to 2017 Dollars (Click to zoom in)</h3>
        </div>
        <div class='step textContainer' id='' data-step-no="pchincb0016a17">

            <p class='subtitle'>Although African-American incomes rose in some census tracts, the majority of tracts saw median household income for African-Americans fall.</p>
            <h3 class='title'>Percent Change in Household Income for African-American Population between 2000 and 2016, Adjusted to 2017 Dollars (Click to zoom in)</h3>
        </div>
      </Scrollama>
    </mq-layout>

    <mq-layout mq='mobile'>
      <div class='mobileContainer'>
        <h3 id='home' class='m-title'>Gross Rent as Percent of Household Income in 2016</h3>
        <durhamMap initValue='grprchi16'/>
        <p class='m-text'>Regardless of where you look in the city, renters pay a large share of their incomes on housing costs. In fact, almost half of all households in the Raleigh-Durham region spent 30% or more of their monthly income on rent or mortgage payments.</p>
        <h3 class='m-title'>Morgage Monthly Owners Cost as a Percent of Household Income in 2016</h3>
        <durhamMap initValue='mmocphi16'/>
        <p class='m-text'>Although owners are less cost burdened than renters, many homeowners still pay 30% or more of their monthly incomes on housing costs.</p>
        <h3 class='m-title'>Percent change in Median Home Value, 2000-2016 in 2017 dollars</h3>
        <durhamMap initValue='pcmhmval0016a17'/>
        <p class='m-text'>As downtown Durham has become more popular as a place to live, work, and play, housing values have increased in the central areas of the city, while prices have dropped in farther-afield suburban parts of the city. The areas closest to the border of the county have seen increases in median home value, perhaps due to construction of large, expensive homes on large, suburban tracts.</p>

        <h3 class='m-title'>Percent Change in Median Contract Rent between 2000 and 2016, Adjusted to 2017 Dollars</h3>
        <durhamMap initValue='pcmrent0016a17'/>
        <p class='m-text'>We see a similar relationship in this map as with the changes in median home value, although both the increases and decreases in rent seem more dramatic than the changes in home values. The central and downtown areas of the city have seen high rent growth while the close-in suburban areas have seen rents drop. Just as home values increase on the outskirts of the county, so, too, have these areas experienced significant rent increases, perhaps caused by dramatic growth in Durham’s population.</p>

        <h3 id='population' class='m-title'>Percent Change in Population between 2000-2016</h3>
        <durhamMap initValue='pcpop0016'/>
        <p class='m-text'>Most areas of the city have seen dramatic population growth, one of the factors in rent growth. But this picture changes depending on how you filter the data, especially when considering race.</p>

        <h3 class='m-title'>Percent Change in White Population between 2000-2016</h3>
        <durhamMap initValue='pcnhwht0016'/>
        <p class='m-text'>With some exceptions, the majority of population growth among white residents has occurred in the central parts of the city. The more suburban portions of the city have seen decreases in the white population since 2000.</p>

        <h3 class='m-title'>Percent Change in African-American Population between 2000-2016</h3>
        <durhamMap initValue='pcnhblk0016'/>
        <p class='m-text'>This map is almost the exact inverse of the previous one, suggesting that African-American residents have been leaving and/or displaced from the central areas of Durham and relocating in the more suburban areas of the city.</p>

        <h3 id='income' class='m-title'>Percent Change in Household Income between 2000 and 2016, Adjusted to 2017 Dollars</h3>
        <durhamMap initValue='pchinc0016a17'/>
        <p class='m-text'>Another factor that impacts the affordability of housing is income. This map demonstrates that the central parts and most suburban areas of the city have seen income increases, while everything in between has seen stagnant or decreasing incomes.</p>

        <h3 class='m-title'>Percent Change in Household Income for White Population between 2000 and 2016, Adjusted to 2017 Dollars</h3>
        <durhamMap 
        initValue='pchincw0016a17'/>
        <p class='m-text'>Combined with the population map, this shows that not only did white residents move to more central parts of Durham but their incomes also rose very rapidly, too.</p>

        <h3 class='m-title'>Percent Change in Household Income for African-American Population between 2000 and 2016, Adjusted to 2017 Dollars</h3>
        <durhamMap initValue='pchincb0016a17'/>
        <p class='m-text'>Although African-American incomes rose in some census tracts, the majority of tracts saw median household income for African-Americans fall.</p>
      </div>
    </mq-layout>
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
import Vue from 'vue'
import VueMq from 'vue-mq'

// d3 and map stuff
const d3 = require('d3')
const map = load('components/graphs/durhamtrts-map/mapcartogram')
const tooltip = load('mixins/tooltip')

// Data stuff
// const LTDBACS_DATA_PATH = 'http://127.0.0.1:8000/api/ltdbacs_trts_7016/?format=json'
const LTDBACS_DATA_PATH = 'statics/data/ltdbacs7016tr.json'
var _ = require('lodash')

Vue.use(VueMq, {
  breakpoints: {
    mobile: 450,
    tablet: 900,
    laptop: 1250,
    desktop: Infinity
  }
})

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

<style scoped>
.m-title {
  padding: 1rem;
  margin: 0 auto;
  font-size: 1.5rem;
  max-width: 80vw;
  text-align: center;
}

.m-text {
  padding: 1rem;
  margin: 0 auto;
  font-size: 1rem;
  max-width: 80vw;
  text-align: center;
}
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
