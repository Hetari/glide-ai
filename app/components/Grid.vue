<template>
  <svg
    id="grid"
    xmlns="http://www.w3.org/2000/svg"
    fill="none"
    viewBox="0 0 935 425"
    class="absolute -top-14 -left-2 -z-10 mask-t-from-70% mask-x-from-95% mask-b-from-50%"
  >
    <g class="grid-group">
      <template v-for="i in grid[0]" :key="i">
        <path
          v-for="j in grid[1]"
          :key="j"
          fill="currentColor"
          opacity="0.2"
          class="grid-item"
          :d="`M${(j - 1) * 32 + 5},${(i - 1) * 32 + 10}l1.806,-2.951l-5,2.951l3.936,1.049l-0.742,-1.049z`"
        />
      </template>
    </g>
  </svg>
</template>

<script setup lang="ts">
import gsap from 'gsap';
const grid = [14, 30];

onMounted(() => {
  const prefersReducedMotion = window.matchMedia(
    '(prefers-reduced-motion: reduce',
  ).matches;

  if (prefersReducedMotion) {
    gsap.set('#grid', { opacity: 1 });
    gsap.set('.grid-item', {
      opacity: 0.2,
      scale: 1,
    });
    return;
  }

  gsap.set('.grid-item', {
    opacity: 0,
    transformOrigin: 'center',
    color: '#fff',
  });

  gsap.set('#grid', { opacity: 1 });

  const tl = gsap.timeline();

  tl.to('.grid-item', {
    keyframes: [
      {
        opacity: 0,
        duration: 0,
      },
      {
        opacity: 0.4,
        rotate: '+=180',
        color: '#0284c7',
        scale: 3,
        duration: 0.5,
        stagger: {
          amount: 2,
          grid: grid,
          from: 'center',
        },
      },
      {
        opacity: 0.2,
        rotate: '+=180',
        color: '#fff',
        scale: 1,
        delay: -2,
        duration: 0.5,
        stagger: {
          amount: 3,
          grid: grid,
          from: 'center',
        },
      },
    ],
  });

  // Loop Animation
  tl.to('.grid-item', {
    delay: 8,
    repeat: -1,
    repeatDelay: 8,
    keyframes: [
      {
        opacity: 0.4,
        rotate: '+=180',
        color: '#0284c7',
        scale: 3,
        duration: 0.5,
        stagger: {
          amount: 2,
          grid: grid,
          from: 'center',
        },
      },
      {
        opacity: 0.2,
        rotate: '+=180',
        color: '#fff',
        scale: 1,
        delay: -2,
        duration: 0.5,
        stagger: {
          amount: 3,
          grid: grid,
          from: 'center',
        },
      },
    ],
  });
});
</script>
