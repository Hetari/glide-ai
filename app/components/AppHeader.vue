<template>
  <header class="p-4 md:p-6">
    <nav
      aria-label="Main"
      aria-labelledby="main"
      class="mx-auto flex max-w-6xl flex-col justify-between py-2 md:flex-row md:items-center"
    >
      <div class="flex items-center justify-between">
        <NuxtLink
          class="z-50"
          :to="data.header.logoLink.href"
          :title="data.header.logoLink.title"
          @click="isOpen = false"
        >
          <img
            aria-label="Logo"
            src="public/svg/Logo.svg"
            loading="lazy"
            alt="Logo"
            class="h-8 w-auto md:h-10"
          />
          <span class="sr-only">{{ data.seo.site.title }} Home Page</span>
        </NuxtLink>

        <button
          class="block p-2 text-3xl md:hidden"
          :aria-expanded="isOpen"
          @click="isOpen = true"
        >
          <Icon name="ph:list-bold" />
        </button>
      </div>

      <!-- Mobile nav  -->
      <div
        class="fixed inset-0 z-40 flex flex-col items-end bg-gray-950 pt-6 pr-4 transition-transform duration-300 ease-in-out will-change-transform md:hidden"
        :class="isOpen ? 'translate-x-0' : 'translate-x-full'"
      >
        <button class="block p-2 text-3xl" @click="isOpen = false">
          <Icon name="ph:x-bold" />
        </button>
        <ul class="grid justify-items-end gap-6">
          <li v-for="(link, index) in data.header.navLinks" :key="index">
            <NuxtLink
              :to="link.href"
              :title="link.title"
              class="block min-h-11 px-3 text-3xl first:mt-8"
            >
              {{ link.title }}
            </NuxtLink>
          </li>
          <li>
            <button>
              <a
                class="button-link block min-h-11 items-center !px-8 !py-4 text-3xl"
                href="https://github.com/hetari"
                target="_blank"
                rel="noopener noreferrer"
              >
                <Icon name="ph:github-logo-duotone" class="mr-2" />
                GitHub
              </a>
            </button>
          </li>
        </ul>
      </div>

      <!-- Laptop nav -->
      <ul class="hidden gap-6 md:flex md:items-center">
        <li v-for="(link, index) in data.header.navLinks" :key="index">
          <NuxtLink
            :to="link.href"
            :title="link.title"
            class="inline-flex min-h-11 items-center"
          >
            {{ link.title }}
          </NuxtLink>
        </li>
        <li>
          <button>
            <a
              class="button-link items-center"
              href="https://github.com/hetari"
              target="_blank"
              rel="noopener noreferrer"
            >
              <Icon name="ph:github-logo-duotone" class="mr-2" />
              GitHub
            </a>
          </button>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script lang="ts" setup>
import data from '~/data';

const isOpen = ref(false);
// defineProps<>();
</script>
