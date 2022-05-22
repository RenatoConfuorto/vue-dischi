<template>
  <div class="music-list-section">
    <div class="container">
      <div class="music-list" v-if="musicData.success">
        <MusicFilter @filterMusic="getFilterGenreKey($event)" :objData="genresData" />
        <MusicFilter @filterMusic="getFilterAuthorKey($event)" :objData="authorsData" />
        <div class="row row-cols-1 row-cols-sm-2 row-cols-md-4 row-cols-lg-5">
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
      albumGenreFilterKey: '',
      albumAuthorFilterKey: '',
      genresData: {
        type: 'genere',
        data: [],
      },
      authorsData: {
        type: 'artisti',
        data: [],
      },
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

      this.getAlbumElements(this.authorsData.data, 'author'); //ottenere gli artisti
      this.getAlbumElements(this.genresData.data, 'genre'); //ottenere i generi

    });

    
  },
  methods: {
    getFilterGenreKey(event) {
      this.albumGenreFilterKey = event.toLowerCase();
    },
    getFilterAuthorKey(event) {
      this.albumAuthorFilterKey = event.toLowerCase();
    },

    getAlbumElements(array, key){
      //ottenere degli elementi (artisti o genere) dagli album
      array.push(''); //c'è bisogno anche duìi una stringa vuota
      this.musicData.response.forEach(element => {
      if(!array.includes(element[key])){
        array.push(element[key]);
      }
    });
    
    }
  },
  computed: {
    filteredAlbums() {
      //filtrare per genere
      const genreFilteredMusic = this.musicData.response.filter( (element) => {
        return element.genre.toLowerCase().includes(this.albumGenreFilterKey);
      });

      //filtrare per autore
      const authorilteredMusic = genreFilteredMusic.filter( (element) => {
        return element.author.toLowerCase().includes(this.albumAuthorFilterKey);
      });

      // console.log('genere', genreFilteredMusic);
      // console.log('autore', authorilteredMusic);
      return authorilteredMusic;
    },
  }
}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

.music-list-section{
  width: 80%;
  margin: 0 auto;
  padding-top: 30px;

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