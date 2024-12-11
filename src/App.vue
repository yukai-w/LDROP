<template>
  <div id="app">
    <img v-on:click="goTwitter" class="twitter" src="/twitter.png" />
    <img v-on:click="goPump" class="pump" src="/pump.png" />
    <img class="image" src="/image.png" />
    <three-model-viewer/>
    <div class="font_1">
      <div class="title">
        About
      </div>
      <div class="content">
        "Last Drop" is the first MemeCoin utilizing 3D technology, symbolizing resilience and determination. It merges cutting-edge 3D animation with blockchain innovations, exploring new frontiers in digital art and virtual currencies.
      </div>
    </div>
    <div class="font_2">
      <div class="title">
        Roadmap
      </div>
      <div class="content">
        Launch Phase: Design and develop the 3D coin, initial listing on cryptocurrency exchanges.<br/>
Expansion Phase: Grow the community, increase brand visibility, collaborate with art platforms, and introduce limited edition 3D coins.<br/>
Reaching $ 200K Market Cap: Surprise initiatives for all supporters, such as special airdrops and access to an exclusive club with member benefits.
      </div>
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
      window.open('https://x.com/lastdrop_sol', '_blank');
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
</style>
