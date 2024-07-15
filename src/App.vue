<script setup>
import Spaceship from './components/Spaceship.vue';

const spaceships = ['vue', 'vue', 'vue', 'vue'];
</script>

<template>
  <div class="bg-purple-200 h-screen">
    <div v-for="spaceship in spaceships" class="bg-red-200 h-1/4 p-2 relative">
      <Spaceship :name="spaceship" class="absolute left-0/4" />
    </div>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
