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
        <h1>BOOLFIX</h1>
        <div>
            <input type="text" v-model="store.inputText" @keyup.enter="this.$emit('search')">
            <button @click="this.$emit('search')">search</button>
        </div>
    </div>
</template>

<style scoped lang="scss">
.nav{
    height: 70px;
    background-color: rgb(255, 0, 0);
    display: flex;
    justify-content: space-between;
    align-items: center;
}
</style>
