<template>
  <div id="app">
    <GifPicker :gif="gif" @like="like" @dislike="dislike" @loaded="ready"/>
    <br>
    <button @click="newGif" class="button is-link is-rounded">Следущая гифка</button>
    <br>
    <GifList color="success" :msg="'Понравилось'" @del="dellike" :list="likedGifs">Понравилось</GifList>
    <br>
    <GifList color="danger" :msg="'Не понравилось'" @del="deldislike" :list="dislikedGifs">Не понравилось</GifList>
    <PreLoader v-if="loading"></PreLoader>
  </div>
</template>

<script>
  import GifPicker from "./components/GifPicker";
  import GifList from "./components/GifList";
  import PreLoader from "./components/preloader";

  export default {
    name: "App",
    components: {
      GifPicker,
      GifList,
      PreLoader,
    },

    data() {
      return {
        gif: {},
        likedGifs: [],
        dislikedGifs: [],
        loading: true,
      };
    },

    methods: {
      newGif: async function(){
        this.loading = true;
        const token = 'gOWCeRgz7yK37gFUVNns9aXty3WcHViV'
        const response = await fetch(`http://api.giphy.com/v1/gifs/random?api_key=${token}`)
        const json = await response.json()
        let url = json.data.url
        let src = json.data.image_url
        let name = json.data.title
        this.gif = {'url': src, 'realUrl': url, 'name': name}
      },
      like: function(gif){
          this.likedGifs.push(gif)
          this.newGif()
      },
      dislike: function(gif){
          this.dislikedGifs.push(gif)
          this.newGif()
      },
      ready: function () {
          this.loading = false
      },
      dellike: function (gif) {
        const idx = this.likedGifs.indexOf(gif)
        this.likedGifs.splice(idx,1)
      },
      deldislike: function (gif) {
        const idx = this.dislikedGifs.indexOf(gif)
        this.dislikedGifs.splice(idx,1)
      },
    },
    mounted: function(){
        this.newGif();
    }
  };
</script>

<style>
  #app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
