<template>
  <v-app :style="{background:'#B25AFD'}">
    <v-main>
        <Home/>
    </v-main>
  </v-app>
</template>
<style>
  @import './assets/css/style.css';
</style>

<script>

import Home from './components/Home';
export default {
  name: 'App',

  components: {
    Home
  },

  data: () => ({
    //
  }),
};
</script>
