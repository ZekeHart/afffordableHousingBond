<template>
    <header class='header'>
        <div class='banner-colour'>
            <div class='menu-btn-cnt' @click='showOnClick()'>
                <button class='menu-btn'>Menu</button>
            </div>
            <img class='c4d-logo' 
            src='https://bean-project-screenshots.s3.amazonaws.com/c4d-wht-red.png'
            alt='Code for Durham'/>
            <div
            class='logo-cnt'>
                <a href='https://codefordurham.com/project/affordable-housing/'
                target=_blank rel=_noopener><img
                v-scroll="handleScroll"
                class='logo' src='https://bean-project-screenshots.s3.amazonaws.com/c4d_logo-2.png' alt='Code for Durham logo'/></a>
            </div>
            <nav class='navContainer'>
                <ul class='ulNav'>
                    <li><a class='liItem' target=_blank rel=_noopener href='http://www.dcovotes.com/voters/voting/polling-locations'>Polling stations</a></li>
                    <li class='henlo'>|</li>
                    <li><a class='liItem' target=_blank rel=_noopener href='https://www.durhamaffordablehousingbond.com/'>More information</a></li>
                </ul>
            </nav>
            </div>
             <nav class='navBar'>
                <transition name="fade">
                    <ul
                    v-if='isActive'
                    :class='{ active : isActive, notActive : notActive }'>
                        <li class='liNav'><a @click='showOnClick()' class='navOptions' id='hou' href='#home'>Housing costs</a></li>
                        <li class='liNav'><a @click='showOnClick()' class='navOptions' id='pop' href='#population'>Population change</a></li>
                        <li class='liNav'><a @click='showOnClick()' class='navOptions' id='inc' href='#income'>Income change</a></li>
                        <li class='liNav'><a @click='showOnClick()' class='navOptions' id='comp' href='#comparison'>See other cities</a></li>
                        <li class='liNav'><a @click='showOnClick()' class='navOptions' id='conc' href='#conclusion'>Our conclusion</a></li>
                    </ul>
                </transition>
            </nav>
    </header>
</template>

<script>
import Vue from 'vue'

Vue.directive('scroll', {
  inserted: function (el, binding) {
    let f = function (evt) {
      if (binding.value(evt, el)) {
        window.removeEventListener('scroll', f)
      }
    }
    window.addEventListener('scroll', f)
  }
})

export default {
  name: 'Headers',
  data: () => {
    return {
      isActive: false,
      notActive: true,
      pushBull: false
    }
  },
  methods: {
    showOnClick () {
      this.isActive = !this.isActive
      this.notActive = !this.notActive
      this.pushBull = true
    },
    handleScroll: function (evt, el) {
      if (window.scrollY > 50) {
        el.setAttribute(
          'style',
          'opacity: 1; transition: all ease .5s; transform: translate3d(0, -62px, 0)'
        )
      }
      return window.scrollY > 100
    }
  }
}
</script>
<style>
@import url('https://fonts.googleapis.com/css?family=Lato&display=swap');
@import url('https://fonts.googleapis.com/css?family=Playfair+Display:900&display=swap');
/* $lato: 'Lato', sans-serif;
$play: 'Playfair Display', serif; */

.navContainer {
    height: inherit;
    display: flex;
    justify-content: center;
    align-items: center;
}
.ulNav {
    display: flex;
    margin-left: 30vh;
    list-style: none;
}

.liItem {
    color: #fff;
    cursor: pointer;
    align-self: center;
    font-family: 'Lato', sans-serif;
    font-size: 1.2rem;
    text-transform: uppercase;
    z-index: 99;
    position: relative;
}

.liItem:after {
    content: "";
    display: block;
    width: 0;
    height: 1px;
    bottom: 0;
    left: 50%;
    border-bottom: 1px solid #fff;
    transition: 1s;
}

.liItem:hover:after {
    width: 100%;
}

.henlo {
    padding-left: 10px;
    padding-right: 10px;
    font-family: 'Lato', sans-serif;
    font-size: 1.2rem;
    text-transform: uppercase;
    color: #fff;
}
.liItem:hover {
    color: #fff;
}

.c4d {
    font-family: 'Lato', sans-serif;
    color: #fff;
    font-size: 2.5rem;
    margin-left: 10vh;
    align-self: center;
}

.c4d-logo {
    width: 30%;
    margin-left: 9vh;
}

.active {
    transition: 2s;
    padding-top: 85px;
    width: 16%;
    position: fixed;
    display: block;
    background: #399aca;
    list-style-type: none;
    padding-inline-start: 0;
    margin-block-start: 0;
    margin-block-end: 0;
    z-index: 88;
}

/* .active.v-enter, .active.v-leave {
    height: 0;
    padding: 0 10px;
    opacity: 0;
} */
.notActive {
    display: none;
}

.menu-btn-cnt {
    z-index: 99;
    cursor: pointer;
    position: relative;
    height: inherit;
    display: flex;
    align-items: center;
    width: 12vh;
    justify-content: center;
    background-color: #B30513;
}

.menu-btn {
    margin: auto;
    align-self: center;
    z-index: 99;
    font-size: 1.2rem;
    cursor: pointer;
    background: transparent;
    border: none;
    color: #fff;
    /* font-size: 2rem; */
    /* letter-spacing: .5em; */
    padding: 0;
    text-transform: uppercase;
    position: relative;
}

.menu-btn:after {
    content: "";
    display: block;
    width: 0;
    height: 1px;
    bottom: 0;
    left: 50%;
    border-bottom: 1px solid #fff;
    transition: .5s;
}

.menu-btn:hover:after {
    width: 2.7em;
}

.header {
    padding-bottom: 15vh;
}

.logo-cnt {
    width: inherit;
    height: inherit;
    position: absolute;
    z-index: 3;
    display: flex;
    justify-content: center;
}
.logo {
    margin-top: 1vh;
    /* align-self: flex-end; */
    height: 125px;
    border-radius: 50%;
}

.banner-colour {
    display: flex;
    filter: drop-shadow(2px 2px 2px #639bb6);
    /* align-items: center; */
    /* background-image: linear-gradient(to right, #399aca, #5442f5); */
    background-color: #399aca;
    width: 100vw;
    height: 70px;
    position: fixed;
    z-index: 95;
}

.navOptions {
    position: relative;
    color: #fff;
    font-size: 1rem;
    z-index: 99;
    border-bottom: 1px #fff solid;
    font-family: 'Lato', sans-serif;
    text-transform: uppercase;
}

/* .navOptions:hover:before {
    transform: scaleX(1);
    visibility: visible;
} */

.navOptions:after {
    content: "";
    position: absolute;
    height: 1px;
    bottom: 0;
    /* left: -10; */
    transition: 1s;
    /* visibility: hidden;
    transform: scaleX(0); */
}

.navOptions:hover {
    color: #fff;
    position: relative;
}

.liNav {
    padding-left: 2vh;
    align-self: flex-end;
    padding-bottom: 10%;
}

.textContainer {
    margin: auto;
}


html {
    scroll-behavior: smooth;
}

.fade-enter-active, .fade-leave-active {
  transition: all .8s;
}
.fade-enter, .fade-leave-to {
  /* height: 0; */
  padding-top: 0;
  transform: translateY(-400px);
}

/* .woosh-enter-active, .woosh-leave-active {
  transition: opacity .5s ease;
}
.woosh-enter, .woosh-leave-to {
  opacity: 0;
} */

/* test */

/* * {
    box-sizing: border-box;
    margin: 0;
}

html {
    scroll-behavior: smooth;
}

.navBar {
    background-image: linear-gradient(to right, #399aca, #5442f5);
    width: 100vw;
    height: 10vh;
    position: fixed;
    z-index: 99;
}
a {
    text-decoration: none;
    color: inherit;
}

.logo {
    height: 10vh;
}

ul {
    display: flex;
    justify-content: center;
    width: inherit;
    height: inherit;
    list-style-type: none;
}

.navOptions {
    margin: auto;
    color: #fff;
    font-size: 1rem;
    border-bottom: .1rem solid #fff;
    font-family: 'Lato', sans-serif;
    text-transform: uppercase;
}


.mainContainer {
    display: grid;
    justify-content: center;
}

.textContainer {
    margin: auto;
}

#lorem-title {
    margin-top: 10%;
}
.title {
    font-family: 'Playfair Display', serif;
    font-size: 4rem;
    color: #2f3159;
    text-align: center;
    padding: 10%;
    width: 40vw;
}

.text {
    color: #2b2b2b;
    font-size: 1.5rem;
    line-height: 175%;
    padding: 5%;
    font-family: 'Lato', sans-serif;
    text-align: center;
    width: 40vw;
} */
/* 
// .halfContainer {
//     display: flex;
// }
.mapImg {
    // width: 40vw;
    padding-top: 10%;
    // padding-bottom: 5%;
    height: 85vh;
} */

/* .intro,
.outro {
  padding: 20vh;
} */

/* // additions and overrides of DOM elements vue-scrollama sets up
.scrollama-container {
  display: grid;
  grid-template-areas:
    "graphic text";
  
  .scrollama-graphic {
    grid-area: text;
    height: 80vh;
    top: 10vh;
  }
} */

@media only screen and (max-width: 768px) {

    html, body {
        overflow-x: hidden;
    }
    .logo-cnt { 
        display: none;
    }
    .c4d-logo {
        width: 80%;
        margin-left: 1vh;
    }

    .ulNav {
        display: none;
    }
    .active {
        width: 40vw;
        height: 40vh;
    }
}
</style>