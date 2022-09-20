<script setup>
import { RouterLink, RouterView } from "vue-router";
import Header from "./components/Header.vue";
</script>

<template>
  <Header />
  <RouterView />
</template>

<script>
export default {
  components: {
    Header,
  },
};
</script>

<style>
#app {
  width: 100vw;
  height: 100vh;
  /* display: grid;
  grid-template-rows: 100px auto; */
}

a {
  text-decoration: none;
  transition: 0.4s;
  cursor: pointer;
}
</style>
