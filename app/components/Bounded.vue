<template>
  <Component
    :is="as || 'section'"
    class="px-4 py-14 first:!pt-10 md:px-6 md:py-20 lg:py-24"
  >
    <div class="mx-auto flex w-full max-w-6xl flex-col items-center">
      <slot />
    </div>
  </Component>
</template>

<script lang="ts" setup>
defineProps<{
  as?: keyof HTMLElementTagNameMap;
}>();
</script>
