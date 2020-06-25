<template>
  <div id="app">
    <favs-list :beers="favBeers"></favs-list>
    <beers-list :beers="beers"></beers-list>
    <beer-detail :beer="selectedBeer"></beer-detail>
  </div>
</template>

<script>
import { eventBus } from './main.js'
import BeersList from './components/BeersList.vue'
import BeerDetail from './components/BeerDetail.vue'
import FavsList from './components/FavsList.vue'


export default {
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favBeers: []
    }
  },
  name: 'App',
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail,
    "favs-list": FavsList
  },

  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
     this.selectedBeer = beer
    })
    eventBus.$on('added-fav-beer', (beer) => {
     if (!this.favBeers.includes(beer)) this.favBeers.push(beer)
     
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
  margin: 0px;
  margin-bottom: 0px;
  display: flex;
  width: 100%;
  height: 100vh;

  background-image: url("./assets/brewdog-background.png");
  background-size: 100% 100%;
}
</style>
