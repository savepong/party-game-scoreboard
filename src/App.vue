<script setup>
import { ref } from 'vue';
import Spaceship from './components/Spaceship.vue'

const spaceships = ref([
  {
    name: 'AP',
    image: '/src/assets/spaceships/apollo.webp',
    cssClass: 'rotate-45',
    score: 0
  },
  {
    name: 'MF',
    image: '/src/assets/spaceships/mf.webp',
    cssClass: 'rotate-45',
    score: 0
  },
  {
    name: 'VI',
    image: '/src/assets/spaceships/viking.webp',
    cssClass: 'rotate-45',
    score: 0
  },
  {
    name: 'VO',
    image: '/src/assets/spaceships/voyager.webp',
    cssClass: 'rotate-90',
    score: 0
  }
])

function addScore (index) {
  spaceships.value[index].score++
}

</script>

<template>
  <div class="bg-black h-screen">
    <div v-for="(spaceship, index) in spaceships" class="h-1/4 p-2 relative">
      <div :key="index" :class="`inline-flex justify-between gap-6 items-center h-4/5 max-w-full min-w-fit`" :style="{ 'width': (spaceships[index].score * 20) + '%' }" @click="addScore(index)">
        <p class="text-white text-left">
          <h2 class="text-6xl vt323">{{ spaceship.name }}</h2>
          <span class="text-2xl">{{ spaceship.score * 1000 }}</span>
        </p>
        <Spaceship :name="spaceship.name" :image="spaceship.image" :cssClass="spaceship.cssClass" />
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
