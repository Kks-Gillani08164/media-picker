<template>
  <MediaPicker @FilesUpdated="showFiles" />
</template>

<script>
// @ is an alias to /src
import MediaPicker from "@/components/MediaPicker.vue";

export default {
  name: "HomeView",
  components: {
    MediaPicker,
  },

  methods: {
    showFiles(files) {
      console.log(files);
    },
  },
};
</script>
