<template>
  <footer>
    <nav
      aria-label="Footer"
      class="flex flex-col items-center justify-between gap-6 border-t border-gray-600 px-8 py-7 md:flex-row"
    >
      <NuxtLink
        class="z-50"
        :to="data.header.logoLink.href"
        :title="data.header.logoLink.title"
      >
        <img
          src="public/svg/Logo.svg"
          loading="lazy"
          alt="Logo"
          class="h-8 w-auto md:h-10"
        />
        <span class="sr-only">{{ data.seo.title }} Home Page</span>
      </NuxtLink>

      <ul class="flex items-center gap-6">
        <li v-for="(link, index) in data.header.navLinks" :key="index">
          <NuxtLink
            :to="link.href"
            :title="link.title"
            class="inline-flex min-h-11 items-center"
          >
            {{ link.title }}
          </NuxtLink>
        </li>
      </ul>
    </nav>
  </footer>
</template>

<script lang="ts" setup>
import data from "~/data";
</script>
