<script setup lang="ts">
import HomePage from './components/Homepage.vue'
import TeamPage from './components/TeamPage.vue'
</script>

<!--mounted to app id div via typescript-->
<template>
  <header style="padding-top: 10%">
    <HomePage title="STARFIRE FORGE" />
    <hr class="aligncenter" />
  </header>
  <main>
    <div>
      <TeamPage title="MEET THE TEAM" />
    </div>
    <hr class="aligncenter" />
  </main>
  <footer class="aligncenter">
    <h5>© 2026 Starfire Forge. All Rights Reserved.</h5>
  </footer>
</template>
