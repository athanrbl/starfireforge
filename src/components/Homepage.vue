<!-- eslint-disable vue/multi-word-component-names -->
<script setup lang="ts">
defineProps<{
  title: string
}>()
</script>

<template>
  <div class="aligncenter">
    <div class="fadeout">
      <img alt="Starfire Logo" class="logo" src="../assets/logo.svg" width="125" height="125" />
      <h1 class="green">{{ title }}</h1>
    </div>

    <div id="aboutus" class="block fadeout fadein">
      <h3>WHAT WE DO</h3>
      <p>
        Originally formed to create a TTRPG system, the team quickly pivoted to a
        <i>less restrictive</i> approach to game design. <strong>Starfire Forge</strong> is now a
        team of dedicated, talented people, each contributing in their own unique way to create
        tailor-made experiences that engage, amaze, and leave a mark.
        <a href="#members">Meet the team.</a>
      </p>
    </div>

    <div id="minecraft" class="block fadeout fadein">
      <h3>MINECRAFT</h3>
      <p>
        Currently the most active side of the team, we have experienced minecrafters of all kinds.
        From purely In-Game creations such as <a>Building</a> and <a>Terraforming</a>, to
        <a>Modding</a>, <a>Datapacks</a> and <a>Command Creations</a>.
      </p>
    </div>

    <div id="gamedev" class="block fadeout fadein">
      <h3>GAME DEVELOPMENT</h3>
      <p>
        In the future, we want to expand to different virtual experiences, such as video games. As
        of right now, our focus remains on Minecraft.
      </p>
      <p style="color: gray">More coming soon.</p>
    </div>
  </div>
</template>
