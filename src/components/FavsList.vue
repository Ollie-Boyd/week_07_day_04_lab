<template>
  <div class="favs">
      <h3>Favs</h3>
      <ul>
          <li v-for="(beer, index) in beers" :beer="beer" :key="index">{{beer.name}}</li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'favs-list',
    props: ['beers']

}
</script>

<style scoped>
 .favs {width: 25%;

 };
 ul {
 list-style-type: none;
 }
</style>