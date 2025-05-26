<template>
  <div class="position-uranus floating" style="animation-delay: 2s">
    <img :src="uranus" class="planet-uranus" alt="uranus" />
  </div>
</template>

<script lang="ts" setup>
import uranus from "@/assets/uranus.svg";
</script>

<style scoped>
.position-uranus {
  position: absolute;
  top: 30px;
  right: 340px;
}

.planet-uranus {
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
