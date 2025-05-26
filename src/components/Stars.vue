<template>
  <v-container fluid class="pa-0 fill-height">
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
for (let i = 0; i < 9; i++) {
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
    }, 4000 + i * 700);
  });
});
</script>

<style scoped>
.v-sheet.bg-primary {
  position: relative;
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
</style>
