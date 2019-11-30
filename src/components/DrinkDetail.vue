<template>
  <div :class="addClass()">
  <div v-if="drink" class="modal-content">
    <label v-for="detail in drink.drinks">
    <h2>{{detail.strDrink}}</h2>
    <button v-on:click="handleClose" type="button" class="button">x</button>
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
</div>
</template>

<script>
import {eventBus} from "../main.js"

export default {
  name: "drink-detail",
  props: ["drink"],
  methods: {
    addClass(){
      if((this.drink).length == 0){
        return "modal"
      }
    },
    handleClose(){
      eventBus.$emit('close-pop-up', this.drink)
    }
  }
}
</script>

<style lang="css" scoped>
  .modal-content {
      position: fixed;
      top: 40%;
      background-color: white;
      opacity: 80%;
      border: 2px solid black;
      padding: 1rem 1.5rem;
      width: 24rem;
      border-radius: 0.5rem;
     }
  .modal {
    display: none;
  }
  .button {

  }
</style>
