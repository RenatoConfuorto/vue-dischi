<template>
  <div class="genre-filter">
    <label for="genre-filter">Filtra per genere:</label>
    <select name="filter" id="genre-filter" @change="getChange($event)">
      <option value=""></option>
      <option value="rock">rock</option>
      <option value="pop">pop</option>
      <option value="jazz">jazz</option>
      <option value="metal">metal</option>
    </select>
  </div>
</template>

<script>
export default {
  name: 'MusicFilter',
  methods: {
    getChange(event) {
      this.$emit('filterMusic', event.target.value);
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";
.genre-filter{
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