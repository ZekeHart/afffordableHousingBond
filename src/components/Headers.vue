<template>
    <header class='header'>
        <div class='banner-colour'>
            <div class='menu-btn-cnt'>
                <button class='menu-btn' @click='showOnClick()'>Menu</button>
            </div>
            <h2 class='c4d'>Code for Durham</h2>
            <transition name="fade">
                <div
                v-if='!isActive'
                class='logo-cnt'>
                    <a href='https://codefordurham.com/project/affordable-housing/'><img class='logo' src='https://bean-project-screenshots.s3.amazonaws.com/c4d_logo-2.png' alt='Code for Durham logo'/></a>
                </div>
            </transition>
            </div>
             <nav class='navBar'>
                <transition name="fade">
                    <ul class='ulNav'
                    v-if='isActive'
                    :class='{ active : isActive, notActive : notActive }'>
                        <li class='liNav'><a @click='showOnClick()' class='navOptions' href='#population'>Population change</a></li>
                        <li class='liNav'><a class='navOptions' href='#dolor'>Dolor</a></li>
                        <li class='liNav'><a class='navOptions' href='#sit'>Sit</a></li>
                        <li class='liNav'><a class='navOptions' href='#amet'>Amet</a></li>
                    </ul>
                </transition>
            </nav>
    </header>
</template>

<script>
export default {
  name: 'Headers',
  data: () => {
    return {
      isActive: false,
      notActive: true
    }
  },
  methods: {
    showOnClick () {
      this.isActive = !this.isActive
      this.notActive = !this.notActive
    }
  }
}
</script>
<style>
@import url('https://fonts.googleapis.com/css?family=Lato&display=swap');
@import url('https://fonts.googleapis.com/css?family=Playfair+Display:900&display=swap');
/* $lato: 'Lato', sans-serif;
$play: 'Playfair Display', serif; */

.c4d {
    font-family: 'Lato', sans-serif;
    color: #fff;
    font-size: 2.5rem;
    margin-left: 10vh;
    align-self: center;
}

.menu-btn-cnt {
    z-index: 99;
    position: relative;
    height: inherit;
    background-color: #fff;
}

.active {
    transition: 2s;
    padding-top: 13vh;
    width: 15vw;
    position: fixed;
    display: block;
    background: #399aca;
    list-style-type: none;
    padding-inline-start: 0;
    margin-block-start: 0;
    margin-block-end: 0;
    z-index: 88;
}

.active.v-enter, .active.v-leave {
    height: 0;
    padding: 0 10px;
    opacity: 0;
}
.notActive {
    display: none;
}

.menu-btn {
    z-index: 99;
    cursor: pointer;
    margin-top: 4.5vh;
    margin-left: 2vh;
    margin-right: 2vh;
    background: #fff;
    border: none;
    color: #399aca;
    /* font-size: 2rem; */
    /* letter-spacing: .5em; */
    padding: 0;
    text-transform: uppercase;
    position: relative;
}

.menu-btn:after {
    content: "";
    display: block;
    width: 50%;
    height: 1px;
    bottom: 0;
    left: 50%;
    border-bottom: 1px solid #399aca;
    transition: 1s;
}

.menu-btn:hover:after {
    width: 100%;
}

.header {
    padding-bottom: 15vh;
}

.logo-cnt {
    width: inherit;
    position: absolute;
    z-index: 3;
    display: flex;
    justify-content: center;
}
.logo {
    /* margin-top: 3.5vh; */
    align-self: flex-end;
    height: 20vh;
    border-radius: 50%;
}

.banner-colour {
    display: flex;
    /* align-items: center; */
    /* background-image: linear-gradient(to right, #399aca, #5442f5); */
    background-color: #399aca;
    width: 100vw;
    height: 12vh;
    position: fixed;
    z-index: 95;
}

.navOptions {
    position: relative;
    color: #fff;
    font-size: 1rem;
    z-index: 99;
    border-bottom: 1px solid #fff;
    font-family: 'Lato', sans-serif;
    text-transform: uppercase;
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
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

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
</style>