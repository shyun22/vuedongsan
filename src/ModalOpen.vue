<template>
    <div class="black-bg" v-if="modal_open == true">
        <div class="white-bg">
            <img :src="oneroom[click_room].image" style="width=100%">
            <h4>{{ oneroom[click_room].title }}</h4>
            <p>{{ oneroom[click_room].content }}</p>
            <input v-model.number="month">
            <p> {{ month }} 개월 선택함 : {{ oneroom[click_room].price * month }}원</p>
            <button @click="$emit('closeModal')">닫기</button>
        </div>
    </div>

</template>

<script>
export default {
    name: 'ModalOpen',
    data() {
        return {
            month: 1,

        }
    },
    watch: {
        month(a) {
            if (isNaN(a) == true || a == ' ') {
                alert("숫자만 입력하세요");
                this.month = 1;
            }
        },
    },
    props: {
        oneroom: Array,
        click_room: Number,
        modal_open: Boolean,
    },

    beforeUpdate() {
        if (this.month == 2) {
            alert("2개월은 안팔아요")
        }
    },



}
</script>

<style>

</style>