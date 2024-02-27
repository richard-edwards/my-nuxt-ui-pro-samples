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
  alert(JSON.stringify(event.data))
}
</script>
<template>
  <UContainer class="prose">
    <h2>List of names/phone #'s verified by zod schema</h2>
    <p>
      <ul>
        <li>Name should be at least 5-15 characters</li>
        <li>Save button is disabled if data not valid based on schema</li>
      </ul>
    </p>
    <UDivider />
    <UForm :schema="profileSchema" :state="state" @submit="onSubmit">
      <UFormGroup label="Account Name" class="mt-4" name="name">
        <UInput v-model="state.name" placeholder="Your account name" />
      </UFormGroup>

      <UButton type="submit" class="mt-4" :disabled="profileSchema.safeParse(state).success === false">
        Save
      </UButton>
    </UForm>
    <UCard>
      <div>
        <h3>State</h3>
        <pre> {{ JSON.stringify(state, null, 4) }}</pre>
        <h3>Validation</h3>
        <pre> {{ JSON.stringify(profileSchema.safeParse(state), null, 4) }}</pre>
      </div>
    </UCard>
  </UContainer>
</template>
