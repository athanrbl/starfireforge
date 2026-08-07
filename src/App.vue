<script setup lang="ts">
import HomePage from './components/Homepage.vue'
import TeamPage from './components/TeamPage.vue'
</script>

<!--mounted to app id div via typescript-->
<template>
  <header style="margin-top: 10%">
    <HomePage title="STARFIRE FORGE" />
    <hr class="aligncenter" />
  </header>
  <main>
    <div style="margin-top: 5%">
      <TeamPage title="MEET THE TEAM" />
    </div>
  </main>
</template>
