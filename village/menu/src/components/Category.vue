<script setup>
defineProps({
  title: {
    type: String,
    required: true
  },
  items: {
    type: Array,
    required: true
  }
})
</script>

<template>
  <h2 class="display-4">{{ title }}</h2>
</template>
