<template>
  <div v-if="drink" id="info">
    <label v-for="detail in drink.drinks">
    <h2>{{detail.strDrink}}</h2>
    <ul>
      <li v-if="detail.strIngredient1">{{detail.strMeasure1}} {{detail.strIngredient1}}</li>
      <li v-if="detail.strIngredient2">{{detail.strMeasure2}} {{detail.strIngredient2}}</li>
      <li v-if="detail.strIngredient3">{{detail.strMeasure3}} {{detail.strIngredient3}}</li>
      <li v-if="detail.strIngredient4">{{detail.strMeasure4}} {{detail.strIngredient4}}</li>
      <li v-if="detail.strIngredient5">{{detail.strMeasure5}} {{detail.strIngredient5}}</li>
      <li v-if="detail.strIngredient6">{{detail.strMeasure6}} {{detail.strIngredient6}}</li>
      <li v-if="detail.strIngredient7">{{detail.strMeasure7}} {{detail.strIngredient7}}</li>

    </ul>
    <p><i>{{detail.strInstructions}}</i></p>
    </label>
  </div>
</template>

<script>
export default {
  name: "drink-detail",
  props: ["drink"]
}
</script>

<style lang="css" scoped>
  #info {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
  }
</style>
