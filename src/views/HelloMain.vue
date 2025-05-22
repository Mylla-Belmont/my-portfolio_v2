<template>
  <v-container fluid class="pa-0 fill-height">
    <v-sheet class="bg-primary" height="100vh" width="100%">
      <v-row class="fill-height" align="center" justify="space-around">
        <v-col class="mr-8 ml-10" cols="8" sm="8" md="4">
          <div class="custom-text text-secondary font-italic">Hello! I'm</div>
          <div class="custom-name text-secondary">Camila</div>
          <div class="custom-name text-secondary">Belmont</div>
          <div class="custom-text text-secondary">
            Front-End developer, game designer and digital illustrator
          </div>
        </v-col>
        <v-col cols="4" sm="8" md="4">
          <v-sheet class="ml-16" height="400" width="300" rounded="xl" />
        </v-col>
      </v-row>

      <div
        v-for="(star, index) in stars"
        :key="index"
        class="floating-star"
        :class="{ visible: star.visible }"
        :style="{
          top: star.y + '%',
          left: star.x + '%'
        }"
      >
        <img :src="star.image" alt="star" />
      </div>
    </v-sheet>
  </v-container>
</template>

<script lang="ts" setup>
import wideStar from "@/assets/wide.svg";
import thinStar from "@/assets/thin.svg";
import { ref, onMounted } from "vue";

interface Star {
  x: number;
  y: number;
  visible: boolean;
  image: string;
}

const stars = ref<Star[]>([]);

function randomPercent() {
  return Math.random() * 100;
}

function randomImage() {
  const images = [wideStar, thinStar];
  const idx = Math.floor(Math.random() * images.length);
  return images[idx];
}

function distance(star1: Star, star2: Star) {
  const dx = star1.x - star2.x;
  const dy = star1.y - star2.y;
  return Math.sqrt(dx * dx + dy * dy);
}

function createStar(existingStars: Star[] = []): Star {
  let newStar: Star;
  let tries = 0;
  do {
    newStar = {
      x: randomPercent(),
      y: randomPercent(),
      image: randomImage(),
      visible: false
    };
    tries++;
    if (tries > 20) break;
  } while (existingStars.some(s => distance(s, newStar) < 10));
  return newStar;
}

function toggleStar(index: number) {
  stars.value[index].visible = false;

  setTimeout(() => {
    let newStar: Star;
    let tries = 0;
    do {
      newStar = {
        x: randomPercent(),
        y: randomPercent(),
        image: randomImage(),
        visible: false
      };
      tries++;
      if (tries > 20) break;
    } while (stars.value.some((s, i) => i !== index && distance(s, newStar) < 8));

    stars.value[index] = newStar;

    setTimeout(() => {
      stars.value[index].visible = true;
    }, 50);
  }, 1000);
}

// Inicialização
for (let i = 0; i < 8; i++) {
  stars.value.push(createStar(stars.value));
}

onMounted(() => {
  stars.value.forEach((star, i) => {
    setTimeout(() => {
      star.visible = true;
    }, 1000 + i * 200);
  });

  stars.value.forEach((_, i) => {
    setInterval(() => {
      toggleStar(i);
    }, 7000 + i * 700);
  });
});
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

.v-sheet.bg-primary {
  position: relative;
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

@keyframes blink {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.2;
  }
}

.floating-star {
  position: absolute;
  width: 24px;
  height: 24px;
  opacity: 0;
  transition: opacity 1s ease-in-out;
  user-select: none;
  z-index: 0;
}

.floating-star.visible {
  opacity: 1;
}

.floating-star.blinking {
  animation-name: blink;
  animation-timing-function: linear, ease-in-out;
  animation-iteration-count: infinite, infinite;
  animation-duration: 15s, 3s;
}

.v-row {
  position: relative;
  animation: fadeSlideIn 1s ease-out;
  z-index: 1;
}
</style>
