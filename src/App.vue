<template>
  <v-app>
    <v-main>
      <container fluid class="pa-0 fill-height">
        <SiteHeader />
        <HelloMain />
        <AboutMe />
        <!-- <MyFormation /> -->
      </container>
    </v-main>
  </v-app>
</template>

<script lang="ts" setup>
import SiteHeader from "./components/SiteHeader.vue";
import HelloMain from "./views/HelloMain.vue";
import AboutMe from "./views/AboutMe.vue";
import MyFormation from "./views/MyFormation.vue";
</script>
