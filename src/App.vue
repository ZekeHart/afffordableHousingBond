<template>
  <q-layout
    ref="layout"
    :view="layoutStore.view"
    :left-breakpoint="layoutStore.leftBreakpoint"
    :right-breakpoint="layoutStore.rightBreakpoint"
    :reveal="layoutStore.reveal"
    :left-class="{'bg-grey-2': true}"
  >

    <div id="q-app">
      <Header />
      <Intro />
      <main class="mainContainer">
      <mapCartogram />
    <Conclusion />
  </main>
    </div>
  </q-layout>
</template>

<script>
import layoutStore from './store/layout'
import { routes } from 'router/graphs'
import mapCartogram from 'src/components/graphs/durhamtrts-map/index.vue'
import Header from 'src/components/Headers.vue'
import Intro from 'src/components/Intro.vue'
import 'intersection-observer'
import Scrollama from 'vue-scrollama'
import Conclusion from 'src/components/Conclusion.vue'

function load (component) {
  return () => import(`src/${component}.vue`)
}

const map = load('components/graphs/durhamtrts-map/mapcartogram')

import {
  QLayout,
  QToolbar,
  QToolbarTitle,
  QBtn,
  QIcon,
  QList,
  QListHeader,
  QItem,
  QItemMain,
  QSideLink
} from 'quasar'

export default {
  name: 'q-app',
  components: {
    QLayout,
    QToolbar,
    QToolbarTitle,
    QBtn,
    QIcon,
    QList,
    QListHeader,
    QItem,
    QItemMain,
    QSideLink,
    Scrollama,
    mapCartogram,
    Conclusion,
    Intro,
    Header,
    map: map
  },
  data () {
    const v = layoutStore.view
    return {
      layoutStore,
      items: routes,
      layoutvals: v,
      isActive: false,
      test: 'blue'
    }
  },
  methods: {
    changeView () {
      this.isActive = !this.isActive
      if (this.isActive === true) {
        this.layoutvals = 'lhh Lpr lff'
      }
      else if (this.isActive === false) {
        this.layoutvals = 'lHh Lpr lFf'
      }
    }
  },
  computed: {
    changeWatch () {
      const
        layout = `${this.layoutvals}`
      return `${layout}`
    }
  },
  watch: {
    changeWatch (v) {
      layoutStore.view = v
    }
  }
}
</script>
<style src="vue-scrollama/dist/vue-scrollama.css" >
</style>
<style>
h2 {
    font-size: 2.5rem;
}
h3 {
  font-size:1.5rem;
}
</style>
