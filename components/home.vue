<template>
<main class="main container align-items-center justify-content-center">
  <div class="row landing">
    <div class="stars position-absolute col-12 overflow-hidden"></div>
    <div class="twinkling position-absolute col-12 overflow-hidden"></div>
    <div class="jumbotron jumbotron-fluid bg-transparent text-warning container text-center col-12">
      <h1 class="landing__header justify-content-between text-center col-12 mb-5" data-toggle="tooltip" data-placement="top" title="A long time ago in a galaxy far, far away....">Galactic Translator</h1>
      <p class="hero__runner text-center mb-5 mt-5">A Project for UW HTML 300 Course</p>
      <NuxtLink to="/translatorapp" class="landing__link text-center col-4 btn btn-warning py-1 px-4">{{text}}</NuxtLink>
    </div>
  </div>
  <router-view /> <audio class="landing__audio" autoplay loop>
    <source src="/the-force-theme.mp3">
    <p>Your browser doesn't support HTML5 audio. Here is a <a href="https://soundcloud.com/faroutofficial/far-out-the-force-theme-star-wars-cover">link to the audio</a> instead.</p>
  </audio>
</main>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {

  },
  //audio file needing to be inserted through v-bind
  data() {
    return {
      audio: 'src/assets/the-force-theme.mp3',
      text: 'Enter'
    }
  }
}
</script>
<style scoped>
  main {
    background-color: #000;
    font-family: 'Galaxy';
  }

  .stars,
.twinkling {
    position: absolute;
    display: block;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
}
.stars {
    z-index: 0;
    background: #000 url("/stars.png") repeat top center;
}
.twinkling {
    z-index: 1;
    background: transparent url("/twinkling.png") repeat top center;
    animation: move-twink-back 200s linear infinite;
}
a {
    text-decoration: none;
}
.landing__link {
    text-transform: uppercase;
    font-weight: 900;
    color: #000;
    &:hover {
        background: #000;
        color: #ffc107;
        box-shadow: inset 0 0 1px 1px #ffc107, -2px -2px 5px 1px #fff;
        font-family: $galaxy;
        font-size: 1.2rem;
        letter-spacing: 0.2rem;
        text-shadow: 2px 2px 3px #fff;
    }
}
@keyframes move-twink-back {
    from {
        background-position: 0, 0;
    }
    to {
        background-position: -10000px, 5000px;
    }
}
.jumbotron {
    z-index: 1;
    color: gold;
    font-family: SF Distant Galaxy Outline;
    display: grid;
    place-items: center;
    background: #000 url("/stars.png") repeat top center;
    animation: move-twink-back 200s linear infinite;
}
.landing__header {
    z-index: 1;
    text-shadow: 4px 4px 5px #fff, 0 0 2px #fff, 0 0 2px #fff;
    font-size: 5rem;
    text-align: center;
}
.hero__runner {
    z-index: 1;
    text-shadow: 4px 4px 5px #fff, 0 0 2px #fff, 0 0 2px #fff;
    text-align: center;
}
.btn {
    z-index: 1;
    font-family: sans-serif;
    padding: 1rem 2rem;
    background-color: gold;
    border-radius: 10px;
}
a {
    text-decoration: none;
}
landing__audio {
    width: 1px;
    height: 1px;
    background-color: #000;
    left: -10000px;
    top: 0;
}
@media only screen and (max-width: 767px) {
  .landing__header {
    font-size: 2rem;
  }
  
}
</style>