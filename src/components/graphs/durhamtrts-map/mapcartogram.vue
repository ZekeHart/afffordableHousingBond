<!--

It would be great if you color the map by population using data from index.vue

Based on:
  http://bl.ocks.org/rveciana/a2a1c21ca1c71cd3ec116cc911e5fce9
  http://bl.ocks.org/mapsam/6083585


Links:

-->

<template>
  <svg id='chart' width='490' height='540' />
</template>

<script>

// var viewportWidth = document.documentElement.clientWidth
var width = null
var height = null
var centered = null

// Map stuff
const d3 = require('d3')
const topojson = require('topojson')
const d3Cartogram = require('mixins/d3-cartogram')
const d3Colorbar = require('mixins/d3-colorbar')
// Colors stuff
import * as d3Chromatic from 'd3-scale-chromatic'
import { variableOptions } from './ltdbacs_trts_vuevaroptions'
import Vue from 'vue'
import VueMq from 'vue-mq'

const projection = d3.geoMercator()
  .center([-78.7, 36.05])
  .scale(60000)
  .precision(0.1)
const path = d3.geoPath()
  .projection(projection)

const roadsurls = ['roads.572-802.geojson', 'roads.573-802.geojson', 'roads.574-802.geojson', 'roads.575-802.geojson', 'roads.576-802.geojson', 'roads.577-802.geojson', 'roads.572-803.geojson', 'roads.573-803.geojson', 'roads.574-803.geojson', 'roads.575-803.geojson', 'roads.576-803.geojson', 'roads.577-803.geojson', 'roads.572-804.geojson', 'roads.573-804.geojson', 'roads.574-804.geojson', 'roads.575-804.geojson', 'roads.576-804.geojson', 'roads.577-804.geojson', 'roads.572-805.geojson', 'roads.573-805.geojson', 'roads.574-805.geojson', 'roads.575-805.geojson', 'roads.576-805.geojson', 'roads.577-805.geojson']

Vue.use(VueMq, {
  breakpoints: {
    mobile: 450,
    tablet: 900,
    laptop: 1250,
    desktop: Infinity
  }
})

export default {
  data: function () {
    return {
      muniboundaries: null,
      cntyboundaries: null,
      cartogram: null,
      topology: null,
      geometries: null,
      durhamtrts: null,
      durhamhds: null,
      roads: null,
      layer: null,
      colorbar: null
    }
  },
  mounted: function () {
    var mounthis = this
    var dataById

    // console.log(mounthis.initValue)
    mounthis.cartogram = d3Cartogram.d3.cartogram()
      .projection(projection)
      .properties(function (d) {
        return dataById.get(d.id)
      })

    const svg = d3.select(this.$el)
    width = svg.node().getBoundingClientRect().width
    height = width / 2
    // const svg = d3
    // .select("#chart")
    // .append("svg")
    // .attr("viewBox", `0 0 300 600`)

    svg.append('svg')
      .attr('class', 'background')
      .attr('width', width)
      .attr('height', height)

    mounthis.layer = svg.append('g')
      .attr('id', 'layer')
      .attr('transform', 'translate(0,40)')
    mounthis.muniboundaries = mounthis.layer.append('g')
      .attr('id', 'muniboundaries')
      .selectAll('path')
    mounthis.cntyboundaries = mounthis.layer.append('g')
      .attr('id', 'cntyboundaries')
      .selectAll('path')
    mounthis.durhamtrts = mounthis.layer.append('g')
      .attr('id', 'durhamtrts')
      .selectAll('path')
    mounthis.roads = mounthis.layer.append('g')
      .attr('id', 'roads')
      .selectAll('path')
    mounthis.durhamhds = mounthis.layer.append('g')
      .attr('id', 'durhamhds')
      .selectAll('path')
    mounthis.colorbar = mounthis.layer.append('g')
      .attr('class', 'vertical')
      .attr('transform', 'translate(100, 20)')

    // Add municipal boundaries
    d3.json('statics/data/muniboundaries.topojson', function (topology) {
      let geojson = topojson.feature(topology, topology.objects.muniboundaries)

      mounthis.muniboundaries
        .data(geojson.features)
        .enter()
        .append('path')
        .attr('d', path)
        .attr('class', 'muniboundary')
    })
    // Add county boundaries
    d3.json('statics/data/cntyboundaries.topojson', function (topology) {
      let geojson = topojson.feature(topology, topology.objects.cntyboundaries)

      mounthis.cntyboundaries
        .data(geojson.features)
        .enter()
        .append('path')
        .attr('d', path)
        .attr('class', 'cntyboundary')
    })
    // Add block group features and fill with property values
    d3.json('statics/data/durhamtrts10.topojson', function (topology) {
      mounthis.topology = topology
      mounthis.geometries = mounthis.topology.objects.durhamtrts10.geometries

      // d3.json('http://127.0.0.1:8000/api/ltdbacs_trts_7016/?format=json', function (data) {
      d3.json('statics/data/ltdbacs7016tr.json', function (data) {
        dataById = d3.nest()
          .key(function (d) { return d.id })
          .rollup(function (d) { return d[0] })
          .map(data)

        mounthis.layer.selectAll('.tooltip')
          .data(topojson.feature(mounthis.topology, mounthis.topology.objects.durhamtrts10).features)
          .enter()
          .append('path')
          .attr('class', 'tooltip')
          .attr('d', path)
          .on('mouseover', function (d) {
            mounthis.$emit('durhamtrSelected', d.id)
          })
          .on('mouseout', function (d) {
            mounthis.$emit('durhamtrDeselected', d.id)
          })
          .on('click', mounthis.clicked)

        let features = mounthis.cartogram.features(mounthis.topology, mounthis.geometries)

        mounthis.durhamtrts = mounthis.durhamtrts
          .data(features)
          .enter()
          .append('path')
          .attr('d', path)
          .attr('class', 'durhamtrts')
          .attr('id', function (d) {
            return d.id
          })

        let value = function (d) { return +d.properties[mounthis.initValue] }

        for (var i = 0; i < variableOptions.length; i++) {
          if (variableOptions[i].value === mounthis.initValue) {
            var voptions = variableOptions[i]
          }
        }
        let lo = Math.max(parseFloat(voptions.lo), -100)
        let hi = Math.min(parseFloat(voptions.hi), 100)

        // let colorScale = d3.scaleLinear()
        let colorScale = d3.scaleSequential(d3Chromatic.interpolateRdBu)
          .domain([lo, hi])

        mounthis.durhamtrts.transition()
          .duration(750)
          .ease(d3.easeLinear)
          .attr('fill', function (d) {
            if (isNaN(d.properties[mounthis.initValue])) {
              return '#fff'
            }
            else {
              return colorScale(value(d))
            }
          })

        let tickspace = (hi - lo) / 4
        let cbV = d3Colorbar.d3
          .colorbarV(colorScale, 20, 200)
          .tickValues([lo, lo + tickspace, lo + (tickspace * 2), lo + (tickspace * 3), hi])
        mounthis.colorbar.call(cbV)
        mounthis.colorbar.append('text').attr('x', 58).attr('y', 105)
      })
    })
    // Add roads
    for (var i = 0; i < roadsurls.length; i++) {
      d3.json('statics/data/' + roadsurls[i], function (geojson) {
        mounthis.roads
          .data(geojson.features)
          .enter().append('path')
          .attr('d', path)
          .attr('class', 'roads')
          .attr('class', function (d) { return d.properties.kind })
      })
    }
    // Add neighborhood boundaries
    d3.json('statics/data/durhamhds.geojson', function (geojson) {
      // var geojson = topojson.feature(topology, topology.objects.durhamhds)

      mounthis.durhamhds
        .data(geojson.features)
        .enter()
        .append('path')
        .attr('d', path)
        .attr('class', 'durhamhds')
        .attr('visibility', 'hidden')

      mounthis.durhamhds
        .data(geojson.features)
        .enter()
        .append('text')
        .attr('class', 'durhamhds')
        .attr('visibility', 'hidden')
        .each(function (d) {
          if (parseFloat(d.properties.shape_area) < 0.00006) {
            return
          }
          d3.select(this)
            .attr('transform', function (d) { return 'translate(' + path.centroid(d) + ')' })
            .attr('text-anchor', 'middle')
            .style('font-size', '3px')
            .style('fill', '#F3EFEE')
            .text(function (d) { return d.properties.name })
        })
        .filter(function (d) {
          return parseFloat(d.properties.shape_area) < 0.00006
        }).remove()
    })
  },
  props: ['scrollVal', 'initValue'],
  watch: {
    // Retrieve new property value from select in index.html
    scrollVal: function (scrollVal) {
      this.changeScrollVal(scrollVal)
    }
  },
  methods: {
    // Change block groups property value
    changeScrollVal: function (scrollVal) {
      let value = function (d) {
        return +d.properties[scrollVal]
      }
      for (var i = 0; i < variableOptions.length; i++) {
        if (variableOptions[i].value === scrollVal) {
          var voptions = variableOptions[i]
        }
      }
      let lo = Math.max(parseFloat(voptions.lo), -100)
      let hi = Math.min(parseFloat(voptions.hi), 100)

      let colorScale = d3.scaleSequential(d3Chromatic.interpolateRdBu)
        .domain([lo, hi])
      this.durhamtrts.transition()
        .duration(750)
        .ease(d3.easeLinear)
        .attr('fill', function (d) {
          if (isNaN(d.properties[scrollVal])) {
            return '#fff'
          }
          // else if (isNaN(d.properties[this.initValue])) {
          //   return '#fff'
          // }
          else {
            return colorScale(value(d))
          }
        })

      this.colorbar.remove()
      this.colorbar = this.layer.append('g')
        .attr('class', 'vertical')
        .attr('transform', 'translate(100,20)')
      this.colorbar.append('text').attr('x', 45 + (voptions.hi.length * 3)).attr('y', 105).text(voptions.unit)
      console.log('unit', d3Chromatic.interpolateRdBu)
      let tickspace = (hi - lo) / 4
      let cbV = d3Colorbar.d3
        .colorbarV(colorScale, 20, 200)
        .tickValues([hi, hi - tickspace, hi - (tickspace * 2), hi - (tickspace * 3), lo])
      this.colorbar.call(cbV)
    },
    // Click to zoom
    clicked: function (d) {
      let x
      let y
      let k

      if (d && centered !== d) {
        let centroid = path.centroid(d)
        x = centroid[0]
        y = centroid[1]
        k = 4
        centered = d

        d3.selectAll('.durhamhds').attr('visibility', 'visible')
      }
      else {
        x = width / 2
        y = height / 2
        k = 1
        centered = null

        d3.selectAll('.durhamhds').attr('visibility', 'hidden')
      }

      this.layer.selectAll('path')
        .classed('active', centered && function (d) { return d === centered })

      this.layer.transition()
        .duration(750)
        .attr('transform', 'translate(' + width / 2 + ',' + height / 1.75 + ')scale(' + k + ')translate(' + -x + ',' + -y + ')')
        .style('stroke-width', 1.5 / k + 'px')
    }
  }
}
</script>

<style>

#tooltipContainer {
  display: none;
}
.background {
  fill: none;
  pointer-events: all;
}
.muniboundary {
  display: none;
  stroke: gray;
  fill: lightgray;
}
.cntyboundary {
  stroke: gray;
  fill: none;
}
.durhamtrts {
  opacity: 0.9;
  stroke: #98999b;
}
.roads {
  display: none;
  /* fill: none;
  stroke: white;
  stroke-linejoin: round;
  stroke-linecap: round; */
}
.major_road {
  display: none;
  /* fill: none;
  stroke: #fb7b7a;
  stroke-width: 1px;
  stroke-linejoin: round;
  stroke-linecap: round; */
}
.minor_road {
  display: none;
  /* fill: none;
  stroke: #999;
  stroke-width: 0.5px;
  stroke-linejoin: round;
  stroke-linecap: round; */
}
.highway {
  fill: none;
  stroke: blue;
  stroke-width: 1.5px;
  stroke-linejoin: round;
  stroke-linecap: round;
}
.rail {
  display: none;
  fill: none;
  stroke: #503D3F;
  stroke-width: 0.5px;
  stroke-linejoin: round;
  stroke-linecap: round;
}
.path {
  display: none;
  fill: none;
  stroke: brown;
  stroke-width: 0.5px;
  stroke-linejoin: round;
  stroke-linecap: round;
}
.durhamhds {
  fill: none;
  stroke: #164584;
}
.tooltip {
  fill: rgba(255, 255, 255, 0.0);
}
.tooltip:hover {
  fill: steelblue;
  fill-opacity: 0.5;
}
.tooltip:touch {
  fill: steelblue;
  fill-opacity: 0.5;
}

@media only screen and (max-width: 768px) {
  svg {
    left: 400px;
  }
}
</style>
