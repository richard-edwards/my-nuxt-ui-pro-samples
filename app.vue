<script setup>
</script>

<template>
  <UHeader>
    <template #logo>
      My Nuxt UI Pro - Sample Pages
    </template>

    <template #right>
      <UButton to="/" icon="i-heroicons-home-solid" color="gray"
        variant="ghost" />

      <UColorModeButton />

      <UButton to="https://github.com/richard-edwards/my-nuxt-ui-pro-samples"
        target="_blank" icon="i-simple-icons-github" aria-label="GitHub"
        color="gray" variant="ghost" />
    </template>
  </UHeader>

  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>

  <UFooter>
    <template #left>
      Copyright © {{ new Date().getFullYear() }}
    </template>
  </UFooter>
  <UNotifications>
    <template #title="{ title }">
      <span v-html="title" />
    </template>

    <template #description="{ description }">
      <span v-html="description" />
    </template>
  </UNotifications>
</template>
