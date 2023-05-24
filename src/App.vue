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
        .then(response => (this.store.filmList = response.data.results));


      axios.get('https://api.themoviedb.org/3/search/tv',
        {
          params: {
            api_key: 'd7e2fe710e865fed3df9a182fa17dee7',
            query: store.inputText,
          }
        })
        .then(response => (this.store.seriesList = response.data.results));

    },
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
