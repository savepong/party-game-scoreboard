<script setup>
defineProps({
  name: String,
  image: String,
  cssClass: String
})

</script>

<template>
    <img :src="image" :class="`cursor-e-resize h-full ${cssClass}`" :alt="name" />
</template>

<style scoped>

</style>