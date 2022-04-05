<template>
<div>
  <img class="gallery__image" :src="src" :alt="alt" :title="title" v-on:click="myImage(); $emit('click');" :class="{active: isActive}" />
</div>
</template>

<script>
import {
  imageMixin
} from "~/assets/imageMixin.js"

export default {
  name: 'Art',
  // Image Toggle Mixin
  mixins: [imageMixin],
  data() {
    return {
      isActive: false
    }
  },
  props: {
    src: {
      type: String,
      required: true
    },
    alt: {
      type: null,
      required: true
    },
    title: {
      type: null,
      required: true
    }
  },
  methods: {
    doSomething() {
      alert("Hello!");
    },
  }
}
</script>

<style scoped>
img {
  float: left;
  width: 200px;
  height: 200px;
  object-fit: cover;
}

.active {
  box-shadow: 3px -3px 15px 2px #a0f, 3px -3px 30px 2px #f0a;
}
</style>