<template>
  <v-container fluid class="pa-0 fill-height relative-container organic-background">
    <v-row class="fill-height ml-10" align="center" justify="start">
      <v-col cols="6">
        <div class="custom-name text-primary">About Me</div>
        <div class="custom-text text-primary mt-4">
          Lorem Ipsumis simply dummy text... Lorem Ipsumis simply dummy text of the printing and
          typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since
          the 1500s, when an unknown printer took a galley of type and scrambled it to make a type
          specimen book.
        </div>
      </v-col>
    </v-row>
    <Mars />
    <Uranus />
    <Stars />
  </v-container>
</template>

<script lang="ts" setup>
import Mars from "@/components/Mars.vue";
import Uranus from "@/components/Uranus.vue";
import Stars from "@/components/Stars.vue";
</script>

<style scoped>
.organic-background {
  position: relative;
  background-image: url("@/assets/Vector 2@2x.svg");
  background-position: top left;
  background-size: contain;
}

.custom-text {
  font-size: 14px;
  letter-spacing: 1.7px;
}

.custom-name {
  font-size: 40px;
  letter-spacing: 1.7px;
  font-weight: bold;
}
</style>
