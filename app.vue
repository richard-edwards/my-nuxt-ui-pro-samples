<script setup>
const links = [
  {
    label: 'Input Validation',
    to: '/input',
  },
  {
    label: 'Sample',
    to: '/sample',
  },
  {
    label: 'Select Menu',
    to: '/selectmenu',
  },
];
</script>

<template>
  <UHeader :links="links">
    <template #logo> Nuxt UI Pro - My Sample Pages </template>

    <template #right>
      <UButton
        to="/"
        icon="i-heroicons-home-solid"
        color="gray"
        variant="ghost"
      />

      <UColorModeButton />

      <UButton
        to="https://github.com/nuxt-ui-pro/starter"
        target="_blank"
        icon="i-simple-icons-github"
        aria-label="GitHub"
        color="gray"
        variant="ghost"
      />
    </template>
  </UHeader>

  <UMain>
    <NuxtPage />
    <UDivider class="mx-5 my-5" />
    <UButton
      label="Back Home"
      to="/"
      icon="i-heroicons-backspace"
      color="gray"
      variant="ghost"
    />
  </UMain>

  <UFooter>
    <template #left> Copyright © {{ new Date().getFullYear() }} </template>
  </UFooter>
</template>
