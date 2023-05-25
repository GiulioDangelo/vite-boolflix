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
  <div v-show="store.filmList.length != 0">
    <h2>Movies</h2>
    <div class="divider"></div>
  </div>

  <div class="container">

    <div v-for="film in store.filmList" class="card">

      <div class="face front">
        <img v-if="film.poster_path" :src="'http://image.tmdb.org/t/p/w342/' + film.poster_path">

        <img v-else src="https://i.ebayimg.com/images/g/e-MAAOSwDsdhvc7l/s-l1600.jpg" class="placeholder">
      </div>


      <div class="face back">

        <div>
          <h3>Titolo:</h3>
          {{film.title}}
        </div>

        <div>
          <h3>Titolo lingua originale:</h3>
          {{film.original_title}}
        </div>

        <div>
          <h3>Lingua originale:</h3>
          {{ film.original_language }}
        </div>

        <div>
          <h3>overview:</h3>
          {{ film.overview }}
        </div>

        <div class="rating">
          <span v-for="star in Math.ceil(film.vote_average / 2)"> 
            <font-awesome-icon :icon="['fas', 'star']" style="color: #ffd500;" />
          </span>
          
          <span v-for="star in Math.floor(5 - film.vote_average / 2)">
                <font-awesome-icon :icon="['fas', 'star']" />
            </span>
        </div>
      </div>

    </div>
  </div>

</template>

<style scoped lang="scss">
h2{
  color: white;
  font-size: 35px;
  margin: 10px 0px 20px 25px;
}

.divider{
  border: 1px solid white;
}

.container{
  color: white;
  display: flex;
  flex-wrap: wrap;
  max-width: 2000px;
  margin: auto;
}
.face {
	position: absolute;
	width: 100%;
	height: 100%;
	backface-visibility: hidden;
	overflow: hidden;
	transition: .5s;
}

.card{
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  width: 300px;
	height: 450px;
  margin: 10px;
  margin-top: 20px;
  text-align: center;
  border: 1px solid rgb(255, 255, 255);
  border-radius: 10px;
  overflow: hidden;

    .front{
      transform: perspective(600px) rotateY(0deg);
      display: flex;
        img{
          height: 100%;
          position: absolute;
          object-fit: none;
        }
    }
}

.back {
        display: flex;
        flex-direction: column;
        justify-content: center;
        transform: perspective(600px) rotateY(180deg);
        background: rgb(0, 0, 0);
        padding: 15px;
        text-align: center;
        overflow-y: auto;

          div{
            margin-top: 15px;
          }
    }

    .back::-webkit-scrollbar{
   background: rgb(59, 59, 59);
}

.back::-webkit-scrollbar-thumb{
   background: rgb(255, 0, 0);
}

.card:hover .front {
    transform: perspective(600px) rotateY(180deg);
}

.card:hover .back {
    transform: perspective(600px) rotateY(360deg);
}
</style>