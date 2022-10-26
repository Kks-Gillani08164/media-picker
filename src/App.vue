<template>
  <MediaPicker />
</template>

<script>
import MediaPicker from "./components/MediaPicker.vue";

export default {
  name: "App",
  components: {
    MediaPicker,
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
  background-color: #e0e9fa;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
</style>
