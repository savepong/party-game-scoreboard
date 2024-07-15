<script setup>
defineProps({
  name: String,
})

</script>

<template>
    <img :src="`/src/assets/${name}.svg`" class="spaceship h-4/5" :alt="name" />
</template>

<style scoped>
.spaceship {

}
</style>