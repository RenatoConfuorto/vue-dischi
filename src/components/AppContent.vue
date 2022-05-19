<template>
  <div class="app-content d-flex justify-content-center align-items-center">
    <AppMusicList/>
  </div>
</template>

<script>
import AppMusicList from "./AppMusicList.vue";

export default {
  name: 'AppContent',
  components: {
    AppMusicList,
  },
}
</script>

<style lang="scss" scoped>
  @import "../style/variables.scss";

  .app-content{
    width: 100%;
    height: calc(100vh - $app-header-height);
    background-color: $app-primary-color;
  }

</style>