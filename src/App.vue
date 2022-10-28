<template>
  <HomeView></HomeView>
</template>

<script>
import HomeView from "./views/HomeView.vue";
export default {
  name: "App",
  components: {
    HomeView,
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  height: 100vh;

  display: flex;
  align-items: center;
  justify-content: center;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
