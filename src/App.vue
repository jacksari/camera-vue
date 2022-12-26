<template>
  <div id="app">
    <CameraVue @takePicture="takePicture" />
    <PictureVue />
    <br />
    <br />
    <br />
    <h3>Image</h3>
    <img class="image-src" id="image-src" src="" alt="" />
  </div>
</template>

<script>
import CameraVue from './components/Camera.vue';
import PictureVue from './components/Picture.vue';
export default {
  name: "app",
  components: { CameraVue, PictureVue },
  data: function () {
    return {
      stream: null,
    };
  },
  methods: {
    takePicture() {
      console.log("take picture", window.innerWidth);
      let ratio = window.innerHeight < window.innerWidth ? 16 / 9 : 9 / 16;

      const picture = document.querySelector("canvas");
      picture.width = 300;
      picture.height =300;
      const ctx = picture.getContext("2d");
      ctx.imageSmoothingEnabled = true;
      ctx.imageSmoothingQuality = "high";
      ctx.drawImage(
        document.querySelector("video"),
        0,
        0,
        300,
        300
      );
    },
  },
  beforeMount: function () {},
};
</script>

<style>
#app {
  text-align: center;
}
.image-src {
  object-fit: contain;
  height: 300px;
  width: 300px;
  text-align: center;
}
</style>
