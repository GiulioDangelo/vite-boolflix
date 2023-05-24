<script>
import { store } from './../../store'
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
    <div v-for="film in store.filmList" class="card">
      <div>{{film.title}}</div>
      <div>{{film.original_title}}</div>
      <div>{{ film.original_language }}</div>
      <div>{{film.vote_average}}</div>
    </div>
  </div>

</template>

<style scoped lang="scss">
.container{
  display: flex;
  flex-wrap: wrap;
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