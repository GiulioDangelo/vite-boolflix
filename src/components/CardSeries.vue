<script>
import { store } from '../../store'
import LangFlag from 'vue-lang-code-flags';
import axios from 'axios';


export default{
    data() {
        return {
            store,
            castSeries: [],
        }
    },

    components: {
    LangFlag,
  },

methods: {
  getSeriesListCasts(idSeries) {
      axios
        .get(
          `https://api.themoviedb.org/3/movie/${idSeries}/credits`,
          {
            params: {
              api_key: "d7e2fe710e865fed3df9a182fa17dee7",
            },
          },
        )
        .then(
          (response) => {
            const tempSeries = response.data.cast.slice(0, 5);

            this.castSeries = tempSeries

          }
        );
  },
}

}
</script>

<template>

 <div v-show="store.seriesList.length != 0">
    <h2>Series</h2>
    <div class="divider"></div>
  </div>

  <div class="container">

    <div v-for="serie in store.seriesList" class="card">

      <div class="face front">
        <img v-if="serie.poster_path" :src="'http://image.tmdb.org/t/p/w342/' + serie.poster_path">

        <img v-else src="https://i.ebayimg.com/images/g/e-MAAOSwDsdhvc7l/s-l1600.jpg" class="placeholder">
      </div>

      <div class="face back">
        <div>
          <h3>Titolo:</h3>
          {{serie.name}}
        </div>

        <div>
          <h3>Titolo lingua originale:</h3>
          {{serie.original_name}}
        </div>

        <div>
          <h3>Lingua originale:</h3>
          <lang-flag :iso="serie.original_language"/>
        </div>

        <div>
          <h3>overview:</h3>
          {{ serie.overview }}
        </div>

  
        <div class="rating">
          <span v-for="star in Math.ceil(serie.vote_average / 2)">
              <font-awesome-icon :icon="['fas', 'star']" style="color: #ffd500;" />
          </span>
  
          <span v-for="star in Math.floor(5 - serie.vote_average / 2)">
              <font-awesome-icon :icon="['fas', 'star']" />
          </span>
        </div>

        <button @click="this.getSeriesListCasts(serie.id)">CAST</button>

        <ul style="list-style: none" class="cast">
          <li v-for="cast in castSeries">
            {{ cast.name }} IN
            <span style="color: rgba(255, 0, 0, 0.5)">{{ cast.character }}</span>
          </li>
        </ul>

      </div>
    </div>
  </div>
</template>


<style scoped lang="scss">
h2{
  color: white;
  font-size: 40px;
  margin: 100px 0px 20px 25px;
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
  margin-bottom: 20px;
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

    .front{
      transform: perspective(600px) rotateY(0deg);
      display: flex;
        img{
          height: 100%;
          position: absolute;
          object-fit: none;
          border: 1px solid rgb(255, 255, 255);
          border-radius: 10px;
        }
    }
}

.back {
        display: flex;
        flex-direction: column;
        justify-content: center;
        height: 100%;
        transform: perspective(600px) rotateY(180deg);
        background: rgb(0, 0, 0);
        padding: 15px;
        text-align: center;
        overflow-y: auto;
        border: 1px solid rgb(255, 255, 255);
        border-radius: 10px;
        
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
