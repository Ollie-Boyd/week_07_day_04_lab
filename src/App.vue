<template>
  <div id="app">
    <beers-list :beers="beers"></beers-list>
  </div>
</template>

<script>
import { eventBus } from './main.js'
import BeersList from './components/BeersList.vue'

export default {
  data(){
    return {
      beers: [],
      selectedBeer: null
    }
  },
  name: 'App',
  components: {
    "beers-list": BeersList
  },

  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
     this.selectedBeer = beer
    })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
