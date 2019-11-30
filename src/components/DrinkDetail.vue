<template>
  <div v-if="drink">
    <h2>{{drink.drinks[0].strDrink}}</h2>
    <p>{{drink.drinks[0].strInstructions}}</p>
  </div>
</template>

<script>
export default {
  name: "drink-detail",
  props: ["drink"]
}
</script>

<style lang="css" scoped>
</style>
