<template>
  <div>
    <Navbar />
    <About />
    <Footer />
  </div>
</template>

<script>
import About from './About.vue'
import Footer from './Footer.vue'
import Navbar from './Navbar.vue'

export default {
  name: 'LandingPage',
  components: {
    Navbar,
    About,
    Footer,
  },
};
</script>
