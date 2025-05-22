<template>
  <v-app>
    <v-main>
      <SiteHeader />
      <HelloMain />
      <AboutMe />
      <!-- <MyFormation /> -->
    </v-main>
  </v-app>
</template>

<script lang="ts" setup>
import SiteHeader from "./components/SiteHeader.vue";
import HelloMain from "./views/HelloMain.vue";
import AboutMe from "./views/AboutMe.vue";
import MyFormation from "./views/MyFormation.vue";
</script>
