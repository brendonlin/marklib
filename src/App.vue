<template>
  <div id="app">
    <Header></Header>
    <MakrWall></MakrWall>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import MakrWall from "./components/MarkWall.vue";

export default {
  name: "App",
  components: {
    Header,
    MakrWall,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
