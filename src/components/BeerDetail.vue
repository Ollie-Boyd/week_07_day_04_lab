<template>
  <div>
      <h3>Top Beer Faktz</h3>
      <p>Name: {{beer.name}}</p>
      <p>Tagline: {{beer.tagline}}</p>
      <p>Description: {{beer.description}}</p>
      <ul> Food Pairing: 
         <li v-for="food in beer.food_pairing">{{food}}</li>
         </ul>
      <p>ABV: {{beer.abv}}</p>
      <button v-on:click="handleFavClick" >Add to Favourites</button>

  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
    name: 'beer-detail',
    props: ['beer'],
    methods: {
        handleFavClick(){
            eventBus.$emit('added-fav-beer', this.beer)            
        }
    }
}
</script>

<style scoped>

 ul {
 list-style-type: none;
 }
 div {
     width: 50%;
 }
</style>