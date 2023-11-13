<script setup lang="ts">
import { z } from 'zod'
import type { FormSubmitEvent } from '#ui/types'

const profileSchema = z.object({
  name: z.string().min(5, 'Name is too short').max(15, 'Name is too long'),
})

type ProfileSchema = z.output<typeof profileSchema>;

const state = reactive({
  name: undefined,
})

async function onSubmit(event: FormSubmitEvent<ProfileSchema>) {
  // Do something with data
  console.log(event.data)
}
</script>
<template>
  <UContainer class="prose">
    <h3>Sample Notes</h3>
    <p>Validation: Name should be 5-15 characters</p>
    <UDivider />
    <UForm :schema="profileSchema" :state="state" @submit="onSubmit">
      <UFormGroup label="Account Name" class="mt-4" name="name">
        <UInput v-model="state.name" placeholder="Your account name" />
      </UFormGroup>

      <UButton type="submit" class="mt-4">
        Save
      </UButton>
    </UForm>
  </UContainer>
</template>
