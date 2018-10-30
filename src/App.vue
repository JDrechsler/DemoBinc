<template>
  <div id="app">
    <vue-dropzone 
      ref="dropzone" 
      id="drop1" 
      :options="dropOptions"
      @vdropzone-complete="afterComplete"
    ></vue-dropzone>
    <button @click="removeAllFiles">Remove All Files</button>
  </div>
</template>

<script>
import vueDropzone from "vue2-dropzone";

export default {
  data: () => ({
    dropOptions: {
      url: "https://httpbin.org/post",
      maxFilesize: 2, // MB
      maxFiles: 4,
      chunking: true,
      chunkSize: 500, // Bytes
      thumbnailWidth: 150, // px
      thumbnailHeight: 150,
      addRemoveLinks: true
    }
  }),
  components: {
    vueDropzone
  },
  methods: {
    afterComplete(file) {
      console.log(file);
    },
    removeAllFiles() {
      this.$refs.dropzone.removeAllFiles();
    }
  }
};
</script>
