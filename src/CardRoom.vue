<template>
    <div>
        <div>
            <img :src="oneroom.image" calss="room-img">
            <h4 @click="send">{{ oneroom.title }}</h4>
            <p>{{ oneroom.price }}원</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardRoom',
    props: {
        oneroom: Object,
    },
    methods: {
        send() {
            this.$emit('openModal', this.oneroom.id)
        }

    }


}
</script>

<style>

</style>