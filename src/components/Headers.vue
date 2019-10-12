<template>
    <header class='header'>
        <nav class='navBar'>
            <ul class='ulNav'>
                <li><a class='navOptions' href='#lorem'>Code for Durham</a></li>
                <li><img class='logo' src='https://bean-project-screenshots.s3.amazonaws.com/c4d_logo-2.png' alt='Code for Durham logo'/></li>
                <li><a class='navOptions' href='#ipsum'>Ipsum</a></li>
                <li><a class='navOptions' href='#dolor'>Dolor</a></li>
                <li><a class='navOptions' href='#sit'>Sit</a></li>
                <li><a class='navOptions' href='#amet'>Amet</a></li>
            </ul>
        </nav>
    </header>
</template>

<style>
@import url('https://fonts.googleapis.com/css?family=Lato&display=swap');
@import url('https://fonts.googleapis.com/css?family=Playfair+Display:900&display=swap');
/* $lato: 'Lato', sans-serif;
$play: 'Playfair Display', serif; */

.header {
    padding-bottom: 15vh;
}
.logo {
    height: 15vh;
    border-radius: 50%;
}

.navBar {
    /* background-image: linear-gradient(to right, #399aca, #5442f5); */
    background-color: #399aca;
    width: 100vw;
    height: 12vh;
    position: fixed;
    z-index: 99;
}


.navOptions {
    margin: auto;
    color: #fff;
    font-size: 1rem;
    border-bottom: .1rem solid #fff;
    font-family: 'Lato', sans-serif;
    text-transform: uppercase;
}


.ulNav {
    display: flex;
    justify-content: center;
    list-style-type: none;
}

.textContainer {
    margin: auto;
}
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