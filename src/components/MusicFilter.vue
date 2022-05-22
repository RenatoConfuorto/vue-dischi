<template>
  <div class="music-filter">
    <label for="filter">Filtra per {{ objData.type }}:</label>
    <select name="filter" id="filter" @change="getChange($event)">
      <!-- <option value=""></option>
      <option value="rock">rock</option>
      <option value="pop">pop</option>
      <option value="jazz">jazz</option>
      <option value="metal">metal</option> -->
      <option v-for="(item, index) in objData.data" :key="index" :value="item">{{ item }}</option>
    </select>
  </div>
</template>

<script>
export default {
  name: 'MusicFilter',
  methods: {
    getChange(event) {
      // console.log(event.target.value),
      this.$emit('filterMusic', event.target.value);
    }
  },
  props: {
    objData: Object,
  }
}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";
.music-filter{
  padding: 0.3rem;
  margin-bottom: 1rem;
  color: white;
  text-align: center;
  background-color: $app-secondary-color;

  label{
    text-transform: uppercase;
    font-weight: 500;
    margin-right: 10px;
  }

  select{
    text-transform: capitalize;
  }
}

</style>