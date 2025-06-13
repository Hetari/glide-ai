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
  title: data.seo.site.title,
  ogTitle: data.seo.site.title,
  description: data.seo.site.description,
  ogDescription: data.seo.site.description,
  keywords: data.seo.site.keywords.join(', '),
  ogImage: ogImage,
});
</script>
