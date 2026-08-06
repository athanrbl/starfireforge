<script setup lang="ts">
import Homepage from './components/Homepage.vue'
import ProjectPage from './components/ProjectPage.vue'
import TeamPage from './components/TeamPage.vue'
</script>

<!--mounted to app id div via ts script-->
<template>
  <header style="padding-top: 15%;">
    <Homepage msg="Starfire Forge"/>
  </header>
  <main>
    <div style="padding-top: 50%;">
      <ProjectPage/>
    </div>
    <div style="padding-top: 50%; padding-bottom: 100%;">
      <TeamPage/>
    </div>
  </main>
</template>