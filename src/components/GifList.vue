<template>
    <div id="GifList">
        <nav class="panel">
            <p class="panel-heading">{{msg}}</p>
            <div class="panel-block" v-for="gif in list" v-bind:key="gif.name">
                <nav class="level">
                    <div class="level-left">
                        <div class="level-item">
                            <a v-bind:href="gif.realUrl">{{gif.name}}</a>
                        </div>
                    </div>
                    <div class="level-right">
                        <div class="level-item">
                            <a href="#" @click="del(gif)"><i class="fas fa-times-circle"></i></a>
                        </div>
                    </div>
                </nav>
            </div>
        </nav>
    </div>
</template>

<script>
    export default {
        name: "GifList",
        props: ['list', 'msg'],
        methods: {
            del: function (gif) {
                this.$emit('del', gif)
            }
        }

    }
</script>

<style scoped>

</style>
