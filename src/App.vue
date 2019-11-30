<template>
  <div id="app">
    <drinks-list :mocktails="all_drinks.drinks"></drinks-list>
    <drink-detail :drink="drinky"></drink-detail>
  </div>
</template>

<script>
import DrinkDetail from './components/DrinkDetail.vue'
import DrinksList from './components/DrinksList.vue'
import {eventBus} from './main.js'

export default {
  name: 'app',
  data(){
    return{
      all_drinks: [],
      selectedIndex: null,
      drinky: []
    }
  },
  components: {
    "drinks-list": DrinksList,
    "drink-detail": DrinkDetail
  },
  mounted(){
    fetch("https://www.thecocktaildb.com/api/json/v1/1/filter.php?a=Non_Alcoholic")
    .then(res => res.json())
    .then(data => this.all_drinks = data)

    eventBus.$on('drink-selected', (index) => {
      // debugger
      fetch("https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=" + index)
      .then(res => res.json())
      .then(data => this.drinky = data)
    })
  }
}
</script>

<style>

</style>
