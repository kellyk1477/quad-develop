<template>
  <v-app >
    <Navbar />
    <v-main>
      <router-view></router-view>
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import Navbar from './components/Navbar';
import Footer from './components/Footer';

export default {
  name: 'App',

  components: {
    Navbar,
    Footer,
  },

  data: () => ({
    //
  }),
};
</script>

<style lang="scss">

html {
  font-family: 'Inter', sans-serif;
  font-weight: 400;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Inter', sans-serif;
  margin: 0;
  padding: 0;
}

</style>
