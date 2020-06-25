<template>
   <div> 
       <h3>All beers</h3>
    <ul>
        <beers-list-item v-for="(beer, index) in beers" :beer = "beer" :key = "index"></beers-list-item>
    </ul>
  </div>

</template>
    
<script>
import BeersListItem from './BeersListItem'
export default {
    name: 'beers-list',
    props: ['beers'],
    components: {
        "beers-list-item": BeersListItem
    }

}
</script>

<style scoped>

 div {
     width: 25%;
 }
</style>

