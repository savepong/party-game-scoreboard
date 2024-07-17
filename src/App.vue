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
  let count = 0
  const timer = setInterval(function() {
    spaceships.value[index].score += 1
    count++;

    if (count >= 10) {
      clearInterval(timer)
    }
  }, 40)
}

function reduceScore (index) {
  const score = spaceships.value[index].score
  spaceships.value[index].score -= 10
}
</script>

<template>
  <div class="h-screen bg-galaxy bg-black relative">
    <div v-for="(spaceship, index) in spaceships" class="h-1/4 p-4 relative">
      <div :key="index" :class="`inline-flex justify-end gap-4 items-center h-full max-w-full min-w-fit`" :style="{ 'width': spaceships[index].score + '%' }">
        <p class="text-white text-right">
          <h2 class="text-8xl vt323">
            <span v-if="spaceships[index].score >= 100">🏆</span>
            {{ spaceship.name }}
          </h2>
          <button @click="reduceScore(index)" class="w-4 h-4 cursor-w-resize"></button>
          <span class="text-4xl">{{ spaceship.score * 100 }}</span>
        </p>
        <Spaceship @click="addScore(index)" :name="spaceship.name" :image="spaceship.image" :cssClass="spaceship.cssClass" />
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
