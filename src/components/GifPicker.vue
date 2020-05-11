<template>
    <div id="GifPicker">
        <div class="container">
            <div class="level">
                <div class="level-item">
                    <a href="#" class="button is-primary" @click="like"><i class="far fa-thumbs-up fa-2x"></i></a>
                </div>
                <div class="level-item">
                    <img v-bind:src="gif.url" @load="ready" style='height:75%; width:100%; max-width:625px; max-height: 100%;'>
                </div>
                <div class="level-item  ">
                    <a href="#" class="button is-danger" @click="dislike"><i class="far fa-thumbs-down fa-2x"></i></a>
                </div>
            </div>
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
