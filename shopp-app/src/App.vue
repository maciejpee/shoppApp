<template>
  <products-list></products-list>
  <basket></basket>
</template>

<script setup>
    import ProductsList from './components/ProductsList.vue'
    import Basket from './components/Basket.vue'
</script>

<style>
table, th, td {
  border:1px solid black;
  text-align:center
}
</style>

