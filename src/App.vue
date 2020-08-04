<template>
    <v-app >
      <v-main>
        <router-view></router-view>
      </v-main>
    </v-app>
</template>

<script>

export default {
  name: 'App',
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
