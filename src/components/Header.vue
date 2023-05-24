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
        <h1>BOOLFLIX</h1>
        <div>
            <input type="text" v-model="store.inputText" @keyup.enter="this.$emit('search')" placeholder="Search in Boolflix">
            <button @click="this.$emit('search')">Enter</button>
        </div>
    </div>
</template>

<style scoped lang="scss">
.nav{
    height: 70px;
    background-color: rgb(0, 0, 0);
    color: red;
    display: flex;
    justify-content: space-between;
    align-items: center;

    h1{
        margin-inline: 50px;
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
