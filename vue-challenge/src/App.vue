<script setup>
import { ref, watchEffect } from 'vue'

const DUMMY_JSON = 'https://dummyjson.com/products/'
const products = ['1', '20']

const currentProduct = ref(products[0])
const attributes = ref(null)

watchEffect(async () => {
  // this effect will run immediately and then
  // re-run whenever currentBranch.value changes
  const url = `${DUMMY_JSON}${currentProduct.value}`
  attributes.value = await (await fetch(url)).json()
})



</script>

<template>
  
  <template v-for="product in products">
    <input type="radio"
      :id="product"
      :value="product"
      name="product"
      v-model="currentProduct">
    <label :for="product">{{ product }}</label>
  </template>
  <template v-for="attribute in attributes">
    

    <br> {{ attribute }}
    
  </template>
</template>

<style>


</style>