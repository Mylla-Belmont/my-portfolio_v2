<template>
  <v-app-bar color="primary" elevation="0">
    <v-row align="center" no-gutters class="flex-grow-1">
      <v-col cols="auto">
        <v-img
          alt="Logo"
          class="ml-4"
          src="@/assets/Logo-CB.png"
          transition="scale-transition"
          width="60"
          height="60"
          contain
        />
      </v-col>

      <v-col>
        <v-row justify="end" no-gutters>
          <v-col cols="auto" v-for="(label, i) in menuItems" :key="i">
            <v-btn variant="plain">
              <span class="custom-btn text-secondary mx-8">{{ label }}</span>
            </v-btn>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-app-bar>
</template>

<script lang="ts" setup>
import { ref } from "vue";

const menuItems = ref(["Formation", "Occupation", "Portfolio", "Contact"]);
</script>

<style scoped>
.custom-btn {
  font-size: 16px;
  letter-spacing: 1.7px;
  text-transform: capitalize;
}
</style>
