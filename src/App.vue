<template>
  <div>
    <div class="menu">
      <a v-for="a in menu" :key="a">{{ a }}</a>
    </div>
    <div v-for="(a, i) in oneroom" :key="a">
      <img :src="oneroom[i].image" calss="room-img">
      <h4 @click="modal_open = true">{{ oneroom[i].title }}</h4>
      <p>{{ oneroom[i].price }}원</p>
    </div>
  </div>
</template>

<script>
import roomdata from "./assets/oneroom.js"

export default {
  name: 'App',
  data() {
    return {
      oneroom: roomdata,
      modal_open: false,
      menu: ['HOME', 'Shop', 'About']
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}
</style>
