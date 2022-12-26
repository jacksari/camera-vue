<template>
  <div class="camera">
    <video autoplay class="feed"></video>
    <button @click="$emit('takePicture')" class="snap">SNAP</button>
  </div>
</template>

<script>
export default {
  name: "Camera",
  components: {},
  data() {
    return {};
  },
  mounted() {
    this.init();
  },
  methods: {
    init() {
      if (
        "mediaDevices" in navigator &&
        "getUserMedia" in navigator.mediaDevices
      ) {
        let constraints = {
          video: {
            width: {
              min: 640,
              ideal: 1280,
              max: 1920,
            },
            height: {
              min: 360,
              ideal: 720,
              max: 1080,
            },
          },
        };
        navigator.mediaDevices
          .getUserMedia(constraints)
          .then((stream) => {
            const videoPlayer = document.querySelector("video");
            videoPlayer.srcObject = stream;
            videoPlayer.play();
          })
          .catch((err) => {
            console.log(err);
          });
      } else {
        let jr = "not devices";
        console.log(jr);
      }
    },
  },
};
</script>

<style scoped>
.camera {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 2rem;
  box-sizing: border-box;
}
.camera .feed {
  background: #171717;
  width: 100%;
  max-width: 1280px;
  max-height: 80vh;
  box-shadow: 4px 4px 12px 0px rgba(0, 0, 0, 0.25);
}
.snap {
  display: flex;
  width: 75px;
  height: 75px;
  background: orange;
  color: #fff;
  font-weight: bolder;
  border-radius: 50%;
  border: none;
  justify-content: center;
  align-items: center;
  margin-top: 2rem;
  cursor: pointer;
  transition: 0.4s all ease-in-out;
  box-shadow: 4px 4px 12px 0px rgba(0, 0, 2, 0.45);
}

.snap:hover {
  background: orangered;
}
</style>
