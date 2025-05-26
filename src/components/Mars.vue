<template>
  <div class="position-mars floating" style="animation-delay: 0s">
    <img :src="mars" class="planet-mars" alt="mars" />
  </div>
</template>

<script lang="ts" setup>
import mars from "@/assets/mars.svg";
</script>

<style scoped>
.position-mars {
  position: absolute;
  top: 210px;
  right: 50px;
}

.planet-mars {
  width: 150%;
  height: 150%;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.floating {
  animation: float 4s ease-in-out infinite;
}
</style>
