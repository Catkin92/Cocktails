<template>
  <div>
    <li v-on:click="handleClick">
      <img :src="drink.strDrinkThumb" width="150" alt="mocktail">
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
</style>
