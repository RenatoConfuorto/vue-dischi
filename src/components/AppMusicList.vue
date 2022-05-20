<template>
  <div class="music-list-section">
    <div class="container">
      <div class="music-list" v-if="musicData.success">
        <MusicFilter @filterMusic="getFilterAlbum($event)"/>
        <div class="card-container row row-cols-5">
          <MusicCard v-for="(item, index) in filteredAlbums" :key="index" :musicObj="item"/>
        </div>
      </div>
      <div v-else class="loading-screen d-flex justify-content-center">
        <font-awesome-icon icon="fas fa-spinner" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios"
import MusicCard from "./MusicCard.vue";
import MusicFilter from "./MusicFilter.vue";

export default {
  name: 'AppMusicList',
  data() {
    return{
      musicData: {
        response: [],
        success: false,
      },
      albumFilterkey: '',
    }
  },
  components: {
    MusicCard,
    MusicFilter,
  },
  created() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then( (resp) => {
      this.musicData.response = resp.data.response;
      this.musicData.success = true;
    })
  },
  methods: {
    getFilterAlbum(event) {
      this.albumFilterkey = event;
    }
  },
  computed: {
    filteredAlbums() {
      const filteredMusic = this.musicData.response.filter( (element) => {
        return element.genre.toLowerCase().includes(this.albumFilterkey);
      });

      return filteredMusic;
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

.music-list-section{
  width: 80%;

  .loading-screen{
    font-size: 3rem;
    color: white;

      svg{
        animation-timing-function:  linear;
        animation-name: loaderRotation;
        animation-duration: 1s;
        animation-iteration-count: infinite;
      }
  }
}
@keyframes loaderRotation {
  0%{
    transform: rotate(0deg);
  }

  50%{
    transform: rotate(180deg);
    font-size: 150%;
  }

  100%{
    transform: rotate(360deg);
  }
}
</style>