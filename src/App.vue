<template>
  <div id="app">
    <three-model-viewer/>
    <div class="button-container">
      <button onclick="location.href='https://x.com/fartbaby_sol'">
        <img src="/image3.png" alt="Icon">
      </button>
      <button onclick="location.href='https://www.pump.fun'">
        <img src="/image2.png" alt="Icon">
      </button>
    </div>
  </div>
</template>

<script>
import ThreeModelViewer from './components/ThreeModelViewer.vue';

export default {
  name: 'App',
  components: {
    ThreeModelViewer
  },
  methods: {
    goTwitter() {
      window.open('https://x.com/fartbaby_sol', '_blank');

    },
    goPump() {
      window.open('https://pump.fun', '_blank');
    }
  }
}
</script>
<style>
/* 重置页面样式 */
body, html {
  margin: 0;
  padding: 0;
}
.twitter {
  position: absolute;
  left: 10px;
  top: 20px;
  width: 60px;
  height: 60px;
  cursor: pointer;
}
.pump {
  position: absolute;
  left: 100px;
  top: 20px;
  width: 60px;
  height: 60px;
  cursor: pointer;
}
.image {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  bottom: 0;
  height: 200px;
}
.font_1 {
  position: absolute;
  left: 10px;
  top: 50%;
  transform: translateY(-50%);
  width: 200px;
}
.font_1 .title {
  color: red;
  font-weight: 500;
  font-size: 20px;
}
.font_1 .content {
  font-size: 16px;
  color: white;
}
.font_2 {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
  width: 200px;
}
.font_2 .title {
  color: red;
  font-weight: 500;
  font-size: 20px;
}
.font_2 .content {
  font-size: 16px;
  color: white;
}
.button-container {
            position: absolute;
            z-index: 1000;
            left: 50%;
            top: 0;
            transform: translateX(-50%);
            z-index: 10000;
        }
        
        .button-container button {
          width: 60px;
          height: 60px;
          margin-left: 10px;
        }

        .button-container button img {
            /* width: 100%;  */
            height: 59%; 
            object-fit: cover; 
        }
</style>
