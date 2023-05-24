<script>
import { store } from '../../store'
export default{
  data() {
    return {
      store,
    }
  },

  methods: {
    numToStar(){
      star=Math.round(film.vote_average / 2);

      for (let i = star; i < star; i++) {
        
      }
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

      <div class="rating">
        <span v-for="star in Math.ceil(film.vote_average / 2)"> ⭐</span>
      </div>

      <img :src="'http://image.tmdb.org/t/p/w300/' + film.poster_path">
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

.rating{
  display: flex;
}
</style>