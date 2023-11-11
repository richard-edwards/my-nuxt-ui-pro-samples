<script setup>
</script>

<template>
  <UHeader>
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
        to="https://github.com/richard-edwards/my-nuxt-ui-pro-samples"
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
