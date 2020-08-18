<template>
  <div>
    <Navbar />
    <TitleCard />
    <About />
    <Footer />
  </div>
</template>

<script>
import About from './About.vue'
import Footer from './Footer.vue'
import Navbar from './Navbar.vue'
import TitleCard from './TitleCard.vue'

export default {
  name: 'LandingPage',
  components: {
    Navbar,
    About,
    Footer,
    TitleCard,
  },
};
</script>
