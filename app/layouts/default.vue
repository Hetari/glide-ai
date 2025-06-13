<template>
  <main>
    <AppHeader />
    <slot />
    <AppFooter />
  </main>
</template>

<script setup lang="ts">
import data from '~/data';
import ogImage from 'public/assets/ogImage.webp';

useSeoMeta({
  title: data.seo.title,
  ogTitle: data.seo.title,
  description: data.seo.description,
  ogDescription: data.seo.description,
  keywords: data.seo.keywords.join(', '),
  ogImage: ogImage,
});
</script>
