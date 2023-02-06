<template>
  <div>
    <div class="menu">
      <a v-for="a in menu" :key="a">{{ a }}</a>
    </div>

    <DiscountBanner />
    <button @click="priceSort">가격순정렬</button>
    <button @click="sortBack">되돌리기</button>


    <Transition name="fade">
      <ModalOpen @closeModal="modal_open = false" :oneroom="oneroom" :click_room="click_room"
        :modal_open="modal_open" />
    </Transition>

    <CardRoom @openModal="modal_open=true; click_room=$event" :oneroom="oneroom[i]" v-for="(a, i) in oneroom"
      :key="a" />

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
      menu: ['HOME', 'Shop', 'About'],
      oneroomOriginal: [...roomdata],
    }
  },

  methods: {
    priceSort() {
      this.oneroom.sort(function (a, b) {
        return a.price - b.price
      })
    },
    sortBack() {
      this.oneroom = [...this.oneroomOriginal];
    },
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


.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 1s;
}

.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}

.fade-leave-active {
  transition: all 1s;
}

.fade-leave-to {
  opacity: 0;
}
</style>
