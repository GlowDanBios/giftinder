<template>
    <div id="GifPicker">
        <div class="container">
            <a href="#" class="button is-primary" @click="like"><i class="far fa-thumbs-up fa-4x"></i></a>
            <img v-bind:src="gif.url" @load="ready">
            <a href="#" class="button is-danger" @click="dislike"><i class="far fa-thumbs-down fa-4x"></i></a>
        </div>
    </div>
</template>

<script>
    export default {
        name: "GifPicker",
        props: ['gif'],
        methods: {
            like: function () {
                this.$emit('like', this.gif)
            },
            dislike: function () {
                this.$emit('dislike', this.gif)
            },
            ready: function () {
                this.$emit('loaded', true)
            }
        }
    }
</script>

<style scoped>

</style>
