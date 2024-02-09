<script setup>
  const links = [
    {
      label: 'Scratchpad - Anything goes',
      to: '/scratchpad',
      icon: 'i-heroicons-trash',
      badge: 'Testing ground'
    },
    {
      label: 'Select Menu - Select a name',
      to: '/selectmenu',
      icon: 'i-heroicons-home'
    },
    {
      label: 'Input w/ Validation (Zod)',
      to: '/input-simple-zod',
      icon: 'i-heroicons-home'
    },
    {
      label: 'Input List w/ Validation (Zod)',
      to: '/input-list-zod',
      icon: 'i-heroicons-home'
    },
    {
      label: 'Table with Dynamic Columns',
      to: '/table-dynamic-columns',
      icon: 'i-heroicons-table-cells'
    }
  ]
</script>
<template>
  <ULandingHero
    title="My Nuxt-UI Samples"
    description="Just a few samples I have for troubleshooting, current best practice."
  >
    <UVerticalNavigation :links="links" />
  </ULandingHero>
</template>
