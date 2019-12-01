<template>
  <div>
    <h1>Cocktails</h1>

      <select v-on:change="handleSelect" v-model="selectedCategory">
        <option selected disabled placeholder>Categories</option>
        <option v-for="category in categories" :value="category.strCategory">{{category.strCategory}}</option>
      </select>

      <ul>
        <drink v-for="(drink, index) in filteredDrinks" :drink="drink" :key="index"></drink>
      </ul>

  </div>
</template>

<script>
import {eventBus} from '../main.js'
import Drink from './Drink.vue'

export default {
  name: "drinks-list",
  props: ["mocktails", "categories", "filteredDrinks"],
  components: {
    "drink": Drink
  },
  data(){
    return{
    selectedCategory: null
    }
  },
  methods: {
    handleSelect(){
      eventBus.$emit('select-category', this.selectedCategory)
    }
  }
}
</script>

<style lang="css" scoped>

  ul {
    list-style: none;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    padding-left: 0px;
    }
</style>
