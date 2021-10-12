<template>
<div>
  <Header />
  <Display />
  <Footer />
</div>
</template>

<script>
import Display from "@/components/Display.vue";
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";


export default {
  head: {
    title: 'Views from the Galaxy',
    meta: [
      {
        hid: 'description',
        name: 'description',
        content: 'Home page description'
      }
    ],
  },
  name: 'Gallery',
  props: {
    msg: String
  },
  components: {
    Header,
    Display,
    Footer
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>