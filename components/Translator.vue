<template>
<div class="translator__app container-fluid col-12">
  <div class="translator__app--wrapper row row-cols-1 row-cols-sm-2 justify-content-between align-items-center">
    <!-- 	avatar image -->
    <aside class="col-12 col-sm-4 sidebar">
      <figure class="img">
        <img src="~assets/img/c3po.jpg" class="avatar img-fluid" id="c3po">
      </figure>
    </aside>
    <!-- translator interface -->
    <p class="userText">{{ input }}</p>
    <section class="interface__wrapper container">
      <div class="row align-items-center">
        <main class="main-content col-12 rounded" id="main-content">
          <article class="translator col-12   d-flex flex-column justify-content-center align-items-center">
            <h1 class="translator__heading">{{ title }}</h1>
            <div id="prompt" class="translator__prompt bubble">{{ prompt }}</div>
            <form action="" class="translator__form text-center my-3">
              <div id="userInput" class="bubble">
                <textarea v-model.lazy="input" debounce="500" name="ytext" id="ytext" cols="40" rows="12" class="form" placeholder="Please type your text here so C-3P0 can translate it ... for you..."></textarea>
              </div>
              <span id="outPut" class="bubble text-output">{{ translation }}</span>
              <button id="translateButton" type="submit" name="translate" class="hidden btn btn-outline-light my-2 form__button" @click.prevent="getTranslation()">{{ translationbutton }}</button>
            </form>
            <button id="newTranslation" class="btn btn-outline-light my-2 form__button" @click="freshStart()">{{ newtranslationbutton }}</button>
          </article>
          <div class="holo"></div>
        </main>
      </div>
    </section>
  </div>
</div>
</template>

<script>
import image from "~/assets/img/c3po.jpg"

export default {
  name: 'Translator',
  props: {
    msg: String
  },
  data() {
    return {
      input: "",
      message: "Welcome to Vue!",
      image: image,
      alt: "a repaired golden droid",
      title: "Translator",
      prompt: "What text would you like me to translate for you?",
      placeholder: "Please type your text here so C-3P0 can translate it ... for you...",
      translationbutton: "Translate Now",
      newtranslationbutton: "New Translation",
      yodaSpeak: "https://api.funtranslations.com/translate/yoda.json?text=",
      translation: ""
    }
  },
  methods: {
    getTranslation() {
      this.echo = this.yodaSpeak + this.input;
      console.log(this.echo);
      fetch(this.echo)
        .then(async (response) => {
        const data = await response.json();
        const translation = data.contents.translated
      }
        )},
    freshStart() {
      this.input = "",
      console.log(this.input);
    }
  },
  mounted() {
    this.getTranslation()   
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.translator__app {
    display: flex;
    flex-flow: column nowrap;
    justify-content: center;
    align-items: center;
    text-align: center;
    gap: 1rem;
}
.translator__heading {
    font-family: 'Moonhouse';
}
.text-output {
  color: #fff;
  width: 5rem;
  border: 2px solid white;
}
.translator__form {
    display: flex;
    flex-flow: column nowrap;
    justify-content: center;
    align-items: center;
    font-family: 'moderna';
}
.userText {
    color: #c80000;
    border-radius: 4px;
    box-shadow: 1px -1px 15px 1px #0000c9;
    line-height: 1.2rem;
    padding: 0.2rem;
    font-weight: bold;
}
textarea {
    opacity: 1;
    color: yellow;
    letter-spacing: 0.2rem;
    line-height: 1.2rem;
    background-color: #000;
    border: 0 solid #000;
    border-radius: 10px;
    font-family: 'Poppins';
    font-weight: bold;
}
.form__button {
    background-color: grey;
    border-radius: 6px;
    padding: 0.5rem 1rem;
    margin: 1rem;
    font-size: 1.2rem;
    font-family: 'Moonhouse';
    letter-spacing: 0.25rem;
}
.form__button:hover {
    background-color: #0000c9;
    color: #fff;
    font-size: 1rem;
    box-shadow: 1px 1px 10px 2px #fff;
}
.translator__prompt {
    margin-bottom: 1rem;
}
.main {
    background-color: #000;
}
h2 {
    color: blue;
}
/* Styling for Hologram Image */
.avatar {
    max-width: 100%;
    height: auto;
    filter: invert(1) opacity(0.2);
    border-radius: 50%;
}
.avatar:hover {
    filter: invert(0) opacity(0.5);
}
/* Styling for Hologram */
.holo {
    position: relative;
    z-index: 2;
     /* apply this style if you want to put your holo inside */
     /* position: absolute; */
     /* bottom: 0; */
    width: 250px;
    height: 15px;
    margin: -5px auto 0;
    background-color: rgba(#2d8ecf, .35);
    border-radius: 100%;
    filter: blur(2.5px);
    transform: perspective(100px) rotateX(-30deg);
    transform-style: preserve-3d;
    animation: holographic 1.5s infinite alternate;
    backface-visibility: hidden;
}
.holo:after {
        position: absolute;
        left: -10px;
        right: -10px;
        content: "";
        height: 10px;
        background-color: rgba(#2d8ecf, .5);
        border-radius: 100%;
        filter: blur(2.5px);
}

.holo {
        animation-duration: 0.75s;
        opacity: 0.5;
    }
@keyframes float {
    from {
        will-change: unset;
        transform: translateY(-10px);
    }
    to {
        will-change: transform;
        transform: translateY(-30px);
    }
}

@keyframes holographic {
    from {
        will-change: box-shadow;
        box-shadow: 0 -75px 5px rgba(#2d8ecf, .15), 0 -1px 2px rgba(#2d8ecf, .5), 0 -45px 5px rgba(#2d8ecf, .15), 0 -2px 3px rgba(#2d8ecf, .5), 0 -3px 4px rgba(#2d8ecf, .5), 0 -4px 6px rgba(#2d8ecf, .5), 0 -5px 10px rgba(#2d8ecf, .75), 0 -7px 20px rgba(#2d8ecf, .75), 0 -10px 30px rgba(#2d8ecf, .75), 0 -15px 40px rgba(#2d8ecf, .75), 0 -25px 50px rgba(#2d8ecf, .75), 0 -35px 60px rgba(#2d8ecf, .85), 0 -45px 70px rgba(#2d8ecf, .95), 0 -65px 80px rgba(#2d8ecf, 1), 0 -75px 90px rgba(#2d8ecf, 1),;
    }
    to {
        will-change: unset;
        box-shadow: 0 -1px 5px rgba(#2d8ecf, .15), 0 -1px 2px rgba(#2d8ecf, .5), 0 -1px 5px rgba(#2d8ecf, .15), 0 -2px 3px rgba(#2d8ecf, .5), 0 -3px 4px rgba(#2d8ecf, .5), 0 -4px 6px rgba(#2d8ecf, .5), 0 -5px 7px rgba(#2d8ecf, .75), 0 -7px 10px rgba(#2d8ecf, .75), 0 -10px 15px rgba(#2d8ecf, .75), 0 -15px 20px rgba(#2d8ecf, .75), 0 -25px 25px rgba(#2d8ecf, .75), 0 -35px 30px rgba(#2d8ecf, .85), 0 -45px 35px rgba(#2d8ecf, .95), 0 -65px 40px rgba(#2d8ecf, 1), 0 -75px 50px rgba(#2d8ecf, 1),;
    }
}
</style>