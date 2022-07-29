<template>
  <pages-pokemon-vue></pages-pokemon-vue>
</template>

<script>
import pagesPokemonVue from './components/pagesPokemon.vue'

export default {
  name: 'App',
  components: {
   pagesPokemonVue
  }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
 
  margin-top: 60px;
}
</style>
