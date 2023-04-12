<script setup>
import Category from './components/Category.vue';

let menu = [];

fetch('menu.json').then(res => res.json()).then(json => {
  console.log(json);
});
</script>

<template>
  <h1>Menu</h1>
  <Category title="Soft Drinks" :items="menu" />
</template>

<style scoped>

</style>
