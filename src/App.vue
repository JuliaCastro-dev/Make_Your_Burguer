<template>
  <Navbar :logo="logo_src" :alt="app_name" />
  <router-view />
  <Footer />
</template>
<script>
import Navbar from './components/Navbar.vue';
import Footer from './components/Footer.vue';
export default {
  components: {
    Navbar,
    Footer
  },
  data() {
    return {
      logo_src: "/img/logo.png",
      app_name: "Make Your Burguer"

    }
  }
}
</script>

<style>
* {
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS';
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  overflow-x: hidden;
}

.main-container {
  margin: 1vw;
  min-height: 70%;

}

h1 {
  text-align: center;
  font-size: 2vw;
  margin-bottom: 1.2vw;
  color: #222;
}
</style>