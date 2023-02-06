<template>
  <div>
    <div class="menu">
      <a v-for="a in menu" :key="a">{{ a }}</a>
    </div>

    <DiscountBanner/>

    <ModalOpen  @closeModal="modal_open=false" :oneroom="oneroom" :click_room="click_room" :modal_open="modal_open" />

    <!-- <div class="black-bg" v-if="modal_open == true">
      <div class="white-bg">
        <img :src="oneroom[click_room].image" style="width=100%">
        <h4>{{ oneroom[click_room].title }}</h4>
        <p>{{ oneroom[click_room].content }}</p>
        <p>{{ oneroom[click_room].price }}원</p>
        <button @click="modal_open = false">닫기</button>
      </div>
    </div> -->

    <CardRoom @openModal="modal_open=true; click_room=$event" :oneroom="oneroom[i]" v-for="(a, i) in oneroom" :key="a" />
    <!-- <div v-for="(a, i) in oneroom" :key="a">
      <img :src="a.image" calss="room-img">
      <h4 @click="modal_open = true; click_room = i">{{ a.title }}</h4>
      <p>{{ a.price }}원</p>
    </div> -->
  </div>
</template>

<script>
import roomdata from "./assets/oneroom.js"
import DiscountBanner from "./DiscountBanner.vue"
import ModalOpen from "./ModalOpen.vue"
import CardRoom from "./CardRoom.vue"


export default {
  name: 'App',
  data() {
    return {
      click_room: 0,
      oneroom: roomdata,
      modal_open: false,
      menu: ['HOME', 'Shop', 'About']
    }
  },
  components: {
    DiscountBanner,
    ModalOpen,
    CardRoom,

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

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
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

.discount {
  background-color: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
