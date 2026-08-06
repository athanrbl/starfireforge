<script setup lang="ts">
  defineProps<{
    msg: string
  }>()
</script>

<template>
  <div class="aligncenter fadeout">
    <img alt="Starfire Logo" class="logo" src="../assets/logo.svg" width="125" height="125" />
    <h1 class="green">{{ msg }}</h1>
    <h3>
      Minecraft Build and Development Team
    </h3>
    <p>
      See the lorem ipsum or something so that theres tons of text and u can do stuff idk
      i wonder if theres wrapping lets see how long it takes okay there is
    </p>
  </div>
</template>