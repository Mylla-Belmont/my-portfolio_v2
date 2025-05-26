<template>
  <v-container fluid class="pa-0">
    <v-sheet class="bg-primary" height="100vh" width="100%">
      <v-row class="fill-height" align="center" justify="space-evenly">
        <v-col class="mr-8" cols="6" sm="8" md="4">
          <div class="custom-text text-secondary font-italic">Hello! I'm</div>
          <div class="custom-name text-secondary">Camila</div>
          <div class="custom-name text-secondary">Belmont</div>
          <div class="custom-text text-secondary">
            Front-End developer, game designer and digital illustrator
          </div>
        </v-col>
        <v-col cols="4" sm="8" md="4">
          <v-sheet height="400" width="450" rounded="xl" />
        </v-col>
      </v-row>

      <Stars />
    </v-sheet>
  </v-container>
</template>

<script lang="ts" setup>
import Stars from "@/components/Stars.vue";
</script>

<style scoped>
.custom-text {
  font-size: 20px;
  letter-spacing: 1.7px;
}

.custom-name {
  font-size: 80px;
  letter-spacing: 1.7px;
  font-weight: bold;
}

@keyframes fadeSlideIn {
  from {
    opacity: 0;
    transform: translateY(40px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.v-row {
  position: relative;
  animation: fadeSlideIn 1s ease-out;
  z-index: 1;
}
</style>
