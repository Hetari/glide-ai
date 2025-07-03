<template>
  <Bounded>
    <Grid />
    <h1
      id="hero__heading"
      class="mx-auto w-full max-w-3xl text-center text-5xl font-bold text-balance"
    >
      {{ page.heading }}
    </h1>
    <p id="hero__subheading" class="my-4">{{ page.subheading }}</p>
    <div class="mt-8 flex w-full flex-col items-center space-y-8">
      <button
        id="action__button"
        class="group button-link mb-16 items-center gap-2"
        :class="page.cta.iconPosition === 'left' ? 'flex-row-reverse' : ''"
        type="button"
      >
        <a :href="page.cta.href">
          {{ page.cta.title }}
        </a>
        <Icon
          class="transition-all duration-300 ease-in-out group-hover:animate-pulse"
          size="20"
          name="ph:arrow-down"
        />
      </button>

      <div class="glass-container w-fit">
        <div
          class="hero__glow hero__glow__one absolute top-0 left-1/3 -z-10 h-2/3 w-2/3 rounded-full bg-sky-700/50 opacity-0 mix-blend-screen blur-3xl filter md:blur-[120px]"
        />
        <div
          class="hero__glow hero__glow__two absolute top-1/3 left-0 -z-10 h-2/3 w-2/3 rounded-full bg-teal-600/50 opacity-0 mix-blend-screen blur-3xl filter md:blur-[120px]"
        />

        <img
          class="h-auto w-full rounded-3xl shadow drop-shadow-2xl"
          :src="page.cta.image.src"
          :alt="page.cta.image.alt"
        />
      </div>
    </div>
  </Bounded>
</template>

<script setup lang="ts">
import gsap from 'gsap';
import Grid from '~/components/Grid.vue';
import data from '~/data';
const page = data.pages.home;

useSeoMeta({
  title: data.seo.pages.home.title,
  ogTitle: data.seo.pages.home.title,
  description: data.seo.pages.home.description,
  ogDescription: data.seo.pages.home.description,
  ogImage: data.seo.pages.home.image.url,
  ogImageAlt: data.seo.pages.home.image.alt,
  ogImageHeight: data.seo.pages.home.image.height,
  ogImageWidth: data.seo.pages.home.image.width,
});

onMounted(() => {
  const preferReducedMotion = window.matchMedia(
    '(prefers-reduced-motion: reduce)',
  ).matches;

  if (preferReducedMotion) {
    // If the user prefers reduced motion, skip animations
    return;
  }

  const tl = gsap.timeline({
    defaults: {
      ease: 'power2.out',
      repeatDelay: 0,
      delay: 0,
      immediateRender: true,
    },
  });

  tl.fromTo(
    '#hero__heading',
    { scale: 0.5, autoAlpha: 0 },
    { scale: 1, autoAlpha: 1, duration: 1.5 },
  );

  tl.fromTo(
    '#hero__subheading',
    { y: 20, autoAlpha: 0 },
    { y: 0, autoAlpha: 1, duration: 1.2 },
    '-=0.6',
  );

  tl.fromTo(
    '#action__button',
    { y: -20, scale: 1.5, autoAlpha: 0 },
    { y: 0, scale: 1, autoAlpha: 1, duration: 1.3 },
    '-=0.8',
  );

  tl.fromTo(
    ['.glass-container', '.glass-container div'],
    { y: 100, autoAlpha: 0 },
    { y: 0, autoAlpha: 1, duration: 1.5 },
    '-=0.3',
  );

  tl.fromTo(
    '.hero__glow',
    { scale: 0.5, autoAlpha: 0 },
    {
      scale: 1,
      autoAlpha: 1,
      duration: 1.8,
    },
    '-=1',
  );

  tl.to('.hero__glow__one', {
    ease: 'power2.inOut',
    repeat: -1,
    repeatDelay: 0,
    keyframes: [
      { top: '0%', left: '33.33%', duration: 0 },
      { top: '33%', left: '33.33%', duration: 2 },
      { top: '33%', left: '0%', duration: 3 },
      { top: '0%', left: '0%', duration: 2 },
      { top: '0%', left: '33.33%', duration: 3 },
    ],
  });

  tl.to('.hero__glow__two', {
    ease: 'power2.inOut',
    repeat: -1,
    repeatDelay: 0,
    keyframes: [
      { top: '33.33%', left: '0%', duration: 0 },
      { top: '66.66%', left: '0%', duration: 2 },
      { top: '66.66%', left: '33.33%', duration: 3 },
      { top: '33.33%', left: '33.33%', duration: 2 },
      { top: '33.33%', left: '0%', duration: 3 },
    ],
  });
});
</script>
