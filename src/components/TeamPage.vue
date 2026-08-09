<script setup lang="ts">
import { computed, onMounted, onBeforeUnmount, ref } from 'vue'
import 'vue3-carousel/carousel.css'
import { Carousel, Slide, Navigation } from 'vue3-carousel'

defineProps<{
  title: string
}>()

// project team information for card
const members = [
  { name: 'Glued_Galby', tags: ['Building', 'Co-lead'], website: ' ' },
  {
    name: 'King_WolfLIVE',
    tags: ['Building', 'Terraforming', 'Model Artist'],
    website: ' ',
  },
  {
    name: 'Rinkky',
    tags: ['Terraforming', 'Modding', 'Co-lead'],
    website: ' ',
  },
  { name: 'Its_Solara', tags: [' '], website: ' ' },
  {
    name: 'Xi_the_engineer',
    tags: ['Building'],
    website: 'https://linktr.ee/xi_the_engineer',
  },
]

const getMemberImage = (memberName: string) => {
  const imageMap: Record<string, string> = {
    Rinkky: new URL('../assets/Rinkky icon.png', import.meta.url).href,
    Xi_the_engineer: new URL('../assets/Xi_the_engineer icon.png', import.meta.url).href,
    King_WolfLIVE: new URL('../assets/King_WolfLIVE icon.png', import.meta.url).href,
    Glued_Galby: new URL('../assets/Glued_Galby icon.png', import.meta.url).href,
    Its_Solara: new URL('../assets/Its_Solara icon.png', import.meta.url).href,
  }

  return imageMap[memberName] ?? new URL('../assets/logo.png', import.meta.url).href
}

// width-based variables for carouselconfig
const windowWidth = ref(window.innerWidth)
const updateWindowWidth = () => {
  windowWidth.value = window.innerWidth
}

const carouselConfig = computed(() => {
  const width = windowWidth.value // width of page
  let itemsToShow = 2

  if (width >= 1200) itemsToShow = 5
  else if (width >= 900) itemsToShow = 4
  else if (width >= 600) itemsToShow = 3

  const visibleSlides = Math.min(itemsToShow, members.length) // counts the slides
  return {
    itemsToShow: visibleSlides,
    wrapAround: visibleSlides < members.length, // fixes resize issue when running out of slides on wraparound
    autoplay: 5000,
    pauseAutoplayOnHover: true,
    gap: 30,
  }
})

// page width listener for vue
onMounted(() => {
  window.addEventListener('resize', updateWindowWidth)
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', updateWindowWidth)
})
</script>

<template>
  <div id="members" class="aligncenter fadein fadeout">
    <h1 class="green">{{ title }}</h1>
    <Carousel class="membergrid" v-bind="carouselConfig">
      <Slide v-for="member in members" :key="member.name" class="block membercard">
        <div id="memberslide" class="membercardalign">
          <img :src="getMemberImage(member.name)" :alt="member.name" class="memberimg" />
          <h3 style="padding: 0; color: rgb(226, 226, 226)" v-if="member.name === 'Rinkky'">
            {{ member.name }}
            <span class="aligncenter foundertag">Founder</span>
          </h3>
          <h3 style="padding: 0; color: rgb(226, 226, 226)" v-else>
            {{ member.name }}
          </h3>
          <p>{{ member.tags.join(', ') }}</p>
        </div>
        <a v-bind:href="member.website">see more...</a>
      </Slide>
      <template #addons>
        <Navigation />
      </template>
    </Carousel>
  </div>
</template>

<style scoped>
/*the founder tag*/
.foundertag {
  display: inline-flex;
  background-color: green;
  border: 1px solid rgb(9, 73, 0);
  padding: 1px 5px;
  font-size: x-small;
  border-radius: 10px;
  vertical-align: middle;
}

/* card/slide params */
.membercard {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  gap: 0.75rem;
  padding: 1rem 1.25rem;
  width: min(100%, 220px);
  max-width: 240px;
  min-height: 220px;
  text-align: center;
  background-color: #5f5f5f;
  border-radius: 10%;
  box-sizing: border-box;
  overflow-wrap: break-word;
  word-break: break-word;
}

.membercardalign {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

.memberimg {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  object-fit: cover;
  margin: 4px;
}

/*carousel params*/
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
