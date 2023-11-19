<script setup lang="ts">
import { z } from 'zod'
import type { FormSubmitEvent } from '#ui/types'

const schema = z.object({
    password: z.string().min(8),
    confirmPassword: z.string().min(8),
  }).refine((data) => data.password === data.confirmPassword,{
    message: "Passwords don't match",
    path: ["confirmPassword"],
    })

type Schema = z.output<typeof schema>;

const state = reactive({
  password: undefined,
  confirmPassword: undefined
})

async function onSubmit(event: FormSubmitEvent<Schema>) {
  alert(JSON.stringify(event.data))

  console.log(event.data)
}
</script>

<template>
  <UContainer class="prose">
    <h3>Sample Notes</h3>
    <p>Just a scratchpad</p>
    <UDivider />

    <UForm :schema="schema" :state="state" @submit="onSubmit">
      <UFormGroup label="Password" name="password">
        <UInput v-model="state.password" type="password" />
      </UFormGroup>

      <UFormGroup label="Confirm" name="confirmPassword">
        <UInput v-model="state.confirmPassword" type="password" />
      </UFormGroup>

      <UButton type="submit" class="mt-4">
        Submit
      </UButton>
    </UForm>
  </UContainer>
</template>
