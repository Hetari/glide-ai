<template>
  <main>Home</main>
</template>

<script setup lang="ts">
import data from '~/data';

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
