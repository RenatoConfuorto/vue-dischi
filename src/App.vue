<template>
  <div id="app">
    <header>
      <AppHeader/>
    </header>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";

export default {
  name: 'App',
  components: {
    AppHeader,
    }
}
</script>

<style lang="scss">
@import "./style/style.scss";
@import "./style/variables.scss";

</style>
