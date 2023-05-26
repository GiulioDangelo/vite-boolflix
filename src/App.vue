<script>
import axios from 'axios';
import { store } from './../store';
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default{
  data() {
    return {
      store,
    }
  },

  methods: {
    performSearch() {
      axios.get('https://api.themoviedb.org/3/search/movie',
        {
          params: {
            api_key: 'd7e2fe710e865fed3df9a182fa17dee7',
            query: store.inputText,
          }
        })
        .then(response => {this.store.filmList = response.data.results;
        // this.getFilmListCasts() ;
        });


      axios.get('https://api.themoviedb.org/3/search/tv',
        {
          params: {
            api_key: 'd7e2fe710e865fed3df9a182fa17dee7',
            query: store.inputText,
          }
        })
        .then(response => {this.store.seriesList = response.data.results;
        // this.getSeriesListCasts()
        });
 
    },

    // getFilmListCasts() {
    //   for (let i = 0; i < store.filmList.length; i++) {
    //     axios
    //       .get(
    //         `https://api.themoviedb.org/3/movie/${store.filmList[i].id}/credits`,
    //         {
    //           params: {
    //             api_key: "d7e2fe710e865fed3df9a182fa17dee7",
    //           },
    //         },
    //       )
    //       .then(
    //         (response) => {
    //           const tempFilm = response.data.cast.slice(0, 5);

    //           this.store.castFilm[store.filmList[i].id] = tempFilm

    //         }
    //       );
    //   };
    //   console.log(store.cast);
    // },

    // getSeriesListCasts() {
    //   for (let i = 0; i < store.seriesList.length; i++) {
    //     axios
    //       .get(
    //         `https://api.themoviedb.org/3/tv/${store.seriesList[i].id}/credits`,
    //         {
    //           params: {
    //             api_key: "d7e2fe710e865fed3df9a182fa17dee7",
    //           },
    //         },
    //       )
    //       .then(
    //         (response) => {
    //           const tempSeries = response.data.cast.slice(0, 5);

    //           this.store.castSeries[store.filmList[i].id] = tempSeries

    //         }
    //       );
    //   };
    //   console.log(store.castSeries);
    // },

  },

  components: {
    Header,
    Main,
  },

}

</script>

<template>
<Header @search="performSearch"/>
<Main/>
</template>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  @import url('https://fonts.googleapis.com/css2?family=Kanit:ital,wght@0,600;0,700;0,800;0,900;1,600;1,700;1,800;1,900&display=swap');
  font-family: 'Kanit', sans-serif;
}

body{
  background-color: rgb(20, 20, 20);
}
</style>
