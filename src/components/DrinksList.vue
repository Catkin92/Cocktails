<template>
  <div>
    <h1>Mocktails</h1>
      <ul>
        <drink v-for="(drink, index) in mocktails" :drink="drink" :key="index"></drink>
      </ul>
  </div>
</template>

<script>
import Drink from './Drink.vue'

export default {
  name: "drinks-list",
  props: ["mocktails"],
  components: {
    "drink": Drink
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
