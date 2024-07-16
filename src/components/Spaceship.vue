<script setup>
defineProps({
  name: String,
  image: String,
  cssClass: String
})

</script>

<template>
    <img :src="image" :class="`h-full ${cssClass}`" :alt="name" />
</template>

<style scoped>

</style>