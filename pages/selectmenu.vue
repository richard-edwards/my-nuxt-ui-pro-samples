<script setup lang="ts">
import { z } from 'zod';
import type { FormSubmitEvent } from '#ui/types';

const schema = z.object({
  name: z.string('Name is required'),
});

type Schema = z.output<typeof schema>;

const names = ['Steve', 'Richard', 'Pam', 'Dave'];
const state = reactive({
  name: undefined,
});

async function onSubmit(event: FormSubmitEvent<schema>) {
  alert(JSON.stringify(event.data));
  console.log(event.data.name);
}
</script>
<template>
  <UContainer class="prose">
    <h3>Sample Notes</h3>
    <p>Validation: Select a name from the list, name required</p>
    <UDivider />

    <UForm :schema="schema" :state="state" @submit="onSubmit">
      <UFormGroup label="Select something" class="mt-4" name="name">
        <USelectMenu
          v-model="state.name"
          :options="names"
          placeholder="Please select a name"
        >
        </USelectMenu>
      </UFormGroup>

      <UButton type="submit" class="mt-4"> Save </UButton>
    </UForm>
  </UContainer>
</template>
