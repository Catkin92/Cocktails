<template>
  <div>
    <li v-on:click="handleClick">
      <img :src="drink.strDrinkThumb" alt="cocktail">
      <!-- <h4>{{drink.strDrink}}</h4> -->
    </li>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: "drink",
  props: ["drink", "index"],
  methods: {
    handleClick(){
      eventBus.$emit('drink-selected', parseInt(this.drink.idDrink, 10))
    }
  }
}
</script>

<style lang="css" scoped>
  li {
    margin: 2px;
    margin-bottom: 0px;
    margin-top: 1px;
    border: 5px solid white;
  }
  li:hover {
    border: none;
  }
  img {
    width: 100%;
    height: auto;
  }

</style>
