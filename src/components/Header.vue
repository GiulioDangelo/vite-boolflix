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
    <div class="nav">
        <img src="../assets/logo.png" alt="">

        <ul class="list">
            <li>Home</li>
            <li>Serie TV</li>
            <li>FIlm</li>
            <li>Nuovi e Popolari</li>
            <li>La mia Lista</li>
            <li>Sfoglia per lingua</li>
      </ul>

        <div>
            <input type="text" v-model="store.inputText" @keyup.enter="this.$emit('search')" placeholder="Search in Boolflix">
            <button @click="this.$emit('search')">Enter</button>
        </div>
    </div>
</template>

<style scoped lang="scss">
.nav{
    height: 120px;
    background-color: rgb(0, 0, 0);
    color: red;
    display: flex;
    justify-content: space-between;
    align-items: center;

    img{
        margin-inline: 50px;
    }
}

.list{
    list-style: none;
    display: flex;
    justify-content: space-around;
    gap: 2rem;
    color: white;
    li {
      cursor: pointer;
    }
  }
  
input{
    padding: 5px 40px;
    font-size: 17px;
    background-color: rgb(49, 49, 49);
    color: white;
}

button{
    padding:5px 10px;
    font-size: 17px;
    margin-inline: 10px;
}
</style>
