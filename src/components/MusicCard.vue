<template>
  <div class="ms_card-container">
    <div class="ms_card">
      <div class="cover">
        <img :src="musicObj.poster" :alt="musicObj.author">
      </div>
      <div class="info">
        <h3>{{ musicObj.title }}</h3>
        <p>{{ musicObj.author }}</p>
        <p>{{ musicObj.year }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    musicObj: Object,
  }
}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

.ms_card-container{
  margin-bottom: 0.5rem;

  .ms_card{
    height: 100%;
    padding: 0.8rem;
    background-color: $app-secondary-color;

    .cover{
  
      width: 100%;
    }
  
    .info{
       
       h3{
         margin-top: 10px;
         color: white;
         font-size: 1rem;
         text-align: center;
         text-transform: uppercase;
       }

       p{
         margin: 0;
         font-size: 0.8rem;
         text-align: center;
         color: $app-text-color;
       }
    }
  }
}

@media screen and (max-width: 576px) {
  .ms_card-container{
    
    .ms_card{

      .cover{
        width: 75%;
        margin: 0 auto;
      }
    }
  }
}
</style>