<template>
  <div class="music-list">
    <div class="container">
      <div class="row row-cols-5" v-if="musicData.success">
        <MusicCard v-for="(item, index) in musicData.response" :key="index" :musicObj="item"/>
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

export default {
  name: 'AppMusicList',
  data() {
    return{
      musicData: {
        success: false,
      },
    }
  },
  components: {
    MusicCard,
  },
  created() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then( (resp) => {
      this.musicData = resp.data;
    })
  }
}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

.music-list{
  width: 80%;

  .loading-screen{
    font-size: 3rem;
    color: white;

      svg{
        animation-timing-function: linear;
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

  25%{
    transform: rotate(90deg);
  }

  50%{
    transform: rotate(180deg);
    font-size: 150%;
  }

  75%{
    transform: rotate(270deg);
  }

  100%{
    transform: rotate(360deg);
  }
}
</style>