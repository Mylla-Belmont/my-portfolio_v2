<template>
  <v-container fluid class="pa-0 fill-height organic-background">
    <!-- conteúdo aqui -->
  </v-container>
</template>

<script lang="ts" setup>
// Nenhuma lógica reativa por enquanto
</script>

<style scoped>
.organic-background {
  position: relative;
  background-image: url("@/assets/Vector 3.svg");
  background-repeat: no-repeat;
  background-position: bottom left;
  background-size: contain;
  min-height: 100vh; /* Garante que o fundo ocupe toda a tela */
}
</style>
