<script setup lang="ts">
import { computed, onMounted, onBeforeUnmount, ref } from 'vue'
import logo from '../assets/logo.svg'
import 'vue3-carousel/carousel.css'
import { Carousel, Slide, Navigation } from 'vue3-carousel'

defineProps<{
  title: string
}>()

const members = [
  { name: 'Glued_Galby', tags: ['Building', 'Co-lead'] },
  { name: 'King_WolfLIVE', tags: ['Building', 'Terraforming', 'Model Artist'] },
  { name: 'Rinkky', tags: ['Founder', 'Terraforming', 'Modding', 'Co-lead'] },
  { name: 'Its_Solara', tags: [' '] },
  { name: 'Xi_the_engineer', tags: ['Building'] },
]

const windowWidth = ref(window.innerWidth)

const updateWindowWidth = () => {
  windowWidth.value = window.innerWidth
}

onMounted(() => {
  window.addEventListener('resize', updateWindowWidth)
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', updateWindowWidth)
})

const carouselConfig = computed(() => {
  const width = windowWidth.value
  let itemsToShow = 2

  if (width >= 1200) itemsToShow = 5
  else if (width >= 900) itemsToShow = 4
  else if (width >= 600) itemsToShow = 3

  return {
    itemsToShow,
    wrapAround: true,
    autoplay: 5000,
    pauseAutoplayOnHover: true,
    gap: 30,
  }
})
</script>

<template>
  <div id="members" class="aligncenter fadein fadeout">
    <h1 class="green">{{ title }}</h1>
    <Carousel class="membergrid" v-bind="carouselConfig">
      <Slide v-for="member in members" :key="member.name" class="block membercard">
        <img :src="logo" class="memberimg" />
        <h3>{{ member.name }}</h3>
        <p>{{ member.tags.join(', ') }}</p>
        <a href="#">see more...</a>
      </Slide>
      <template #addons>
        <Navigation />
      </template>
    </Carousel>
  </div>
</template>

<style scoped>
.membercard {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.1rem;
  padding: 0.5rem 2rem;
  width: min(100%, 220px);
  max-width: 220px;
  min-height: 180px;
  text-align: center;
  background-color: #5f5f5f;
  border-radius: 10%;
  box-sizing: border-box;
  overflow-wrap: anywhere;
  word-break: break-word;
}

.memberimg {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  object-fit: cover;
}

.carousel {
  max-width: 1280px;
  max-height: 500px;
  width: 100%;
}

.carousel__viewport {
  overflow: hidden;
}

.carousel__slide {
  display: flex;
  justify-content: center;
  box-sizing: border-box;
  padding: 0 0.5rem;
}
</style>
