<template>
  <Bounded>
    <h1
      class="mx-auto w-full max-w-3xl text-center text-5xl font-medium text-balance"
    >
      {{ page.heading }}
    </h1>
    <p class="my-4">{{ page.subheading }}</p>
    <div class="mt-8 flex w-full flex-col items-center space-y-8">
      <button
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
          class="absolute -top-10 left-1/3 -z-10 size-2/3 rounded-full bg-sky-700/50 blur-[100px]"
        />
        <div
          class="absolute -top-0 right-1/3 -z-10 size-2/3 rounded-full bg-teal-700/50 blur-[100px]"
        />

        <div
          class="absolute bottom-10 left-1/3 -z-10 size-2/3 rounded-full bg-red-700/50 blur-[100px]"
        />
        <div
          class="absolute right-1/3 bottom-10 -z-10 size-2/3 rounded-full bg-purple-700/50 blur-[100px]"
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
</script>
