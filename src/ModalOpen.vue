<template>
    <div class="black-bg" v-if="modal_open == true">
        <div class="white-bg">
            <img :src="oneroom[click_room].image" style="width=100%">
            <h4>{{ oneroom[click_room].title }}</h4>
            <p>{{ oneroom[click_room].content }}</p>
            <p>{{ oneroom[click_room].price }}원</p>
            <button @click="$emit('closeModal')">닫기</button>
        </div>
    </div>

</template>

<script>
export default {
    name: 'ModalOpen',
    props: {
        oneroom: Array,
        click_room: Number,
        modal_open: Boolean,
    }

}
</script>

<style>

</style>