<template>
  <div id="app">
    <drink-detail :drink="drink"></drink-detail>
    <drinks-list :filteredDrinks="filteredDrinks.drinks" :categories="categories.drinks" ></drinks-list>
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
      // starter_drinks: [],
      selectedIndex: null,
      drink: [],
      categories: [],
      filteredDrinks: []
    }
  },
  components: {
    "drinks-list": DrinksList,
    "drink-detail": DrinkDetail
  },
  mounted(){
    fetch("https://www.thecocktaildb.com/api/json/v1/1/list.php?c=list")
    .then(res => res.json())
    .then(data => this.categories = data)

    fetch("https://www.thecocktaildb.com/api/json/v1/1/filter.php?c=Ordinary_Drink")
    .then(res => res.json())
    .then(data => this.filteredDrinks = data)

    eventBus.$on('drink-selected', (index) => {
      fetch("https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=" + index)
      .then(res => res.json())
      .then(data => this.drink = data)
    })

    eventBus.$on('close-pop-up', (drink) => {
      this.drink = []
    })

    eventBus.$on('select-category', (category) => {
      fetch("https://www.thecocktaildb.com/api/json/v1/1/filter.php?c=" + category)
      .then(res => res.json())
      .then(data => this.filteredDrinks = data)
    })
  }
}
</script>

<style>
  #app {
    font-family: monospace;
  }
</style>
