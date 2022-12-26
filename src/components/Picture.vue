<template>
<div class="container-picture">
    <div class="picture">
        <canvas id="canvas"></canvas>
    </div>
</div>
  </template>
  
  <script>
  export default {
    name: "Picture",
    components: {  },
    data: function () {
      return {
      };
    },
    methods: {
      
    },
  };
  </script>
  
  <style>
  .container-picture{
    width: 100%;
    display: flex;
    justify-content: center;
    margin-bottom: 4rem;
  }
  .picture{
    width: 100%;
    height: 100%;
    object-fit: cover;
    border: 1px solid orange;
    text-align: center;
  }
  </style>
  