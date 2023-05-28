<script>
import CardMovie from './CardMovie.vue';
import CardSeries from './CardSeries.vue'
import { store } from './../../store'

 
export default{
  data() {
    return {
      store,
    }
  },

  components:{
    CardMovie,
    CardSeries,
  }
}
</script>

<template>
<CardMovie/>
<CardSeries/>
</template>


<style scoped lang="scss">
h2{
  color: white;
  font-size: 40px;
  text-align: center;
  margin-top: 100px;
}
</style>
