<template>
  <div class="music-list">
    <div class="container">
      <div class="row row-cols-5">
        <MusicCard v-for="(item, index) in musicData.response" :key="index" :musicObj="item"/>
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
}

</style>