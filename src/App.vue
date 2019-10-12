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
      <testHeader />
      <main class="mainContainer">
    <Scrollama @step-enter="stepEnterHandler"
        :debug="true">
        <section class='mapImg'  slot='graphic'>
      <mapCartogram />
      </section>
          <section class='textContainer' id='lorem'>
            <h2 id='lorem-title' class='title'>Lorem</h2>

            <p class='text'>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquid cumque non quaerat vitae animi? Assumenda nostrum alias corporis fugiat facilis vero ducimus, beatae aliquam, in perferendis, consectetur saepe unde velit. Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquid cumque non quaerat vitae animi? Assumenda nostrum alias corporis fugiat facilis vero ducimus, beatae aliquam, in perferendis, consectetur saepe unde velit.</p>
        </section>

        <section class='textContainer' id='ipsum'>
            <h2 class='title'>Ipsum</h2>

            <p class='text'>Fixie dirty durham consensus big green wall beaver queen sustainable urban ministries dapper, broad street wool e bull old north innovation bowtie maker, southsquare historic preservation maker full frame sodu the buehler. The bulls hipster blues major sodu duke chapel dino trail eagles, major the state of things ninth street miami boulevard diy. Durham goldenbelt duke park local erwin road saint joseph's, start-up adf miami boulevard bulltown strutters ccb plaza french press, erwin terrace the double nickel merge records elf. Angier drive medicine dance the indy one forty seven train arm wrestling, duke chapel university science and math partner erwin square black wall street major, seventy french press dance dur'm 15-501. Blue devils bouncing bulldogs third fridays the double nickel chapel drive beer doughman seventy west village wunc, northeast central luewwd hipster hub coworking erwin square authentic innovation. Seeds the buehler oprah building walltown arm wrestling historic preservation local, blackwell urban ministries old north the kress historic preservation doughman, trinity park foodie bay 7 eno river bragtown.</p>
        </section>
        <section class='textContainer' id='lorem'>
            <h2 id='lorem-title' class='title'>Lorem</h2>

            <p class='text'>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquid cumque non quaerat vitae animi? Assumenda nostrum alias corporis fugiat facilis vero ducimus, beatae aliquam, in perferendis, consectetur saepe unde velit. Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquid cumque non quaerat vitae animi? Assumenda nostrum alias corporis fugiat facilis vero ducimus, beatae aliquam, in perferendis, consectetur saepe unde velit.</p>
        </section>

        <section class='textContainer' id='ipsum'>
            <h2 class='title'>Ipsum</h2>

            <p class='text'>Fixie dirty durham consensus big green wall beaver queen sustainable urban ministries dapper, broad street wool e bull old north innovation bowtie maker, southsquare historic preservation maker full frame sodu the buehler. The bulls hipster blues major sodu duke chapel dino trail eagles, major the state of things ninth street miami boulevard diy. Durham goldenbelt duke park local erwin road saint joseph's, start-up adf miami boulevard bulltown strutters ccb plaza french press, erwin terrace the double nickel merge records elf. Angier drive medicine dance the indy one forty seven train arm wrestling, duke chapel university science and math partner erwin square black wall street major, seventy french press dance dur'm 15-501. Blue devils bouncing bulldogs third fridays the double nickel chapel drive beer doughman seventy west village wunc, northeast central luewwd hipster hub coworking erwin square authentic innovation. Seeds the buehler oprah building walltown arm wrestling historic preservation local, blackwell urban ministries old north the kress historic preservation doughman, trinity park foodie bay 7 eno river bragtown.</p>
        </section>

    </Scrollama>
      <section class='textContainer' id='lorem'>
            <h2 id='lorem-title' class='title'>Lorem</h2>

            <p class='text'>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquid cumque non quaerat vitae animi? Assumenda nostrum alias corporis fugiat facilis vero ducimus, beatae aliquam, in perferendis, consectetur saepe unde velit. Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquid cumque non quaerat vitae animi? Assumenda nostrum alias corporis fugiat facilis vero ducimus, beatae aliquam, in perferendis, consectetur saepe unde velit.</p>
        </section>

        <section class='textContainer' id='ipsum'>
            <h2 class='title'>Ipsum</h2>

            <p class='text'>Fixie dirty durham consensus big green wall beaver queen sustainable urban ministries dapper, broad street wool e bull old north innovation bowtie maker, southsquare historic preservation maker full frame sodu the buehler. The bulls hipster blues major sodu duke chapel dino trail eagles, major the state of things ninth street miami boulevard diy. Durham goldenbelt duke park local erwin road saint joseph's, start-up adf miami boulevard bulltown strutters ccb plaza french press, erwin terrace the double nickel merge records elf. Angier drive medicine dance the indy one forty seven train arm wrestling, duke chapel university science and math partner erwin square black wall street major, seventy french press dance dur'm 15-501. Blue devils bouncing bulldogs third fridays the double nickel chapel drive beer doughman seventy west village wunc, northeast central luewwd hipster hub coworking erwin square authentic innovation. Seeds the buehler oprah building walltown arm wrestling historic preservation local, blackwell urban ministries old north the kress historic preservation doughman, trinity park foodie bay 7 eno river bragtown.</p>
        </section>
        <section class='textContainer' id='lorem'>
            <h2 id='lorem-title' class='title'>Lorem</h2>

            <p class='text'>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquid cumque non quaerat vitae animi? Assumenda nostrum alias corporis fugiat facilis vero ducimus, beatae aliquam, in perferendis, consectetur saepe unde velit. Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquid cumque non quaerat vitae animi? Assumenda nostrum alias corporis fugiat facilis vero ducimus, beatae aliquam, in perferendis, consectetur saepe unde velit.</p>
        </section>

        <section class='textContainer' id='ipsum'>
            <h2 class='title'>Ipsum</h2>

            <p class='text'>Fixie dirty durham consensus big green wall beaver queen sustainable urban ministries dapper, broad street wool e bull old north innovation bowtie maker, southsquare historic preservation maker full frame sodu the buehler. The bulls hipster blues major sodu duke chapel dino trail eagles, major the state of things ninth street miami boulevard diy. Durham goldenbelt duke park local erwin road saint joseph's, start-up adf miami boulevard bulltown strutters ccb plaza french press, erwin terrace the double nickel merge records elf. Angier drive medicine dance the indy one forty seven train arm wrestling, duke chapel university science and math partner erwin square black wall street major, seventy french press dance dur'm 15-501. Blue devils bouncing bulldogs third fridays the double nickel chapel drive beer doughman seventy west village wunc, northeast central luewwd hipster hub coworking erwin square authentic innovation. Seeds the buehler oprah building walltown arm wrestling historic preservation local, blackwell urban ministries old north the kress historic preservation doughman, trinity park foodie bay 7 eno river bragtown.</p>
        </section>
  </main>
    </div>

    <!-- <q-toolbar slot="footer">
      <q-toolbar-title>
        <div slot="subtitle">
          <a href='http://quasar-framework.org'>Running on Quasar, </a>
          <a href='https://vuejs.org'>Vue,</a>
          <a href='http://www.django-rest-framework.org/'>and Django Rest Framework</a>
        </div>
      </q-toolbar-title>
    </q-toolbar> -->
  </q-layout>
</template>

<script>
import layoutStore from './store/layout'
import { routes } from 'router/graphs'
import mapCartogram from 'src/components/graphs/durhamtrts-map/index.vue'
import testHeader from 'src/components/Headers.vue'
import 'intersection-observer'
import Scrollama from 'vue-scrollama'

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
    testHeader
  },
  data () {
    const v = layoutStore.view
    return {
      layoutStore,
      items: routes,
      layoutvals: v,
      isActive: false
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
.scrollama-container {
  display: grid;
  grid-template-areas:
    "graphic text";
}
  
  .scrollama-graphic {
    grid-area: text;
    height: 80vh;
    top: 10vh;
  }
.mainContainer {
    display: grid;
    justify-content: center;
}

.textContainer {
    margin: auto;
}
</style>
