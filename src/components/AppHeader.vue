<template>
  <div class="header">
    <div class="logo-wrapper">
      <img src="../assets/img/spotify-logo.svg" alt="">
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppHeader',
}
</script>

<style lang="scss" scoped>
  @import "../style/variables.scss";

  .header{
    width: 100%;
    height: $app-header-height;
    background-color: $app-secondary-color;

    .logo-wrapper{
      width: $app-header-height;
      height: $app-header-height;
      display: flex;
      justify-content: center;
      align-items: center;

      img{
        height: 70%;
        width: auto;
      }
    }
  }

</style>