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
    image: '/src/assets/spaceships/mf.gif',
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
    cssClass: 'rotate-45',
    score: 0
  }
])

function addScore (index) {
  spaceships.value[index].score++
}
</script>

<template>
  <div class="h-screen bg-galaxy bg-black relative">
    <div v-for="(spaceship, index) in spaceships" class="h-1/4 p-4 relative">
      <div :key="index" :class="`inline-flex justify-end gap-4 items-center h-full max-w-full min-w-fit`" :style="{ 'width': ((spaceships[index].score + 0.5) * 20) + '%' }" @click="addScore(index)">
        <p class="text-white text-right">
          <h2 class="text-8xl vt323">
            <span v-if="(spaceships[index].score + 0.5) * 20 >= 100">🏆</span>
            {{ spaceship.name }}
          </h2>
          <span class="text-4xl">{{ spaceship.score * 1000 }}</span>
        </p>
        <Spaceship :name="spaceship.name" :image="spaceship.image" :cssClass="spaceship.cssClass" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.bg-galaxy {
  background-image: url("galaxy.jpg");
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
