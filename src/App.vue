<template>
  <div id="app">
    <header>
      <AppHeader/>
    </header>

    <main>
      <AppContent/>
    </main>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppContent from "./components/AppContent.vue";

export default {
  name: 'App',
  components: {
    AppHeader,
    AppContent,
    }
}
</script>

<style lang="scss">
@import "./style/style.scss";
@import "./style/variables.scss";

</style>
