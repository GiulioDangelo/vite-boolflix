<script>
import { store } from '../../store'

export default{
    data() {
        return {
            store,
        }
    },
}
</script>

<template>
  <div class="container">
    <div v-for="serie in store.seriesList" class="card">
      <div>{{serie.name}}</div>
      <div>{{serie.original_name}}</div>
      <div>{{ serie.original_language }}</div>

      <div class="rating">
        <span v-for="star in Math.ceil(serie.vote_average / 2)"> ⭐</span>
      </div>

      <img :src="'http://image.tmdb.org/t/p/w300/' + serie.poster_path">
    </div>
  </div>
</template>


<style scoped lang="scss">
.container{
  display: flex;
  flex-wrap: wrap;
  margin-top: 50px;
  border: 4px solid red;
}
.card{
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  margin: 10px;
  border: 1px solid black;
}
</style>
