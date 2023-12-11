<script setup lang="ts">
  import { z } from 'zod'
  import type { FormSubmitEvent } from '#ui/types'

  interface PhoneListItem {
    name: string
    number: string
  }

  const phoneRegex = new RegExp(
    /^([+]?[\s0-9]+)?(\d{3}|[(]?[0-9]+[)])?([-]?[\s]?[0-9])+$/
  )

  const state = reactive({
    items: [
      { name: 'Home', number: '1-555-123-4567' },
      { name: 'Work', number: '1-555-123-4568' },
      { name: '', number: '' }
    ] as PhoneListItem[]
  })

  const phoneListSchema = z.object({
    items: z.array(
      z.object({
        name: z.string().min(1),
        number: z.string().regex(phoneRegex, 'Invalid Number!')
      })
    )
  })
  type PhoneListSchema = z.output<typeof phoneListSchema>

  async function onSubmit(event: FormSubmitEvent<PhoneListSchema>) {
    // Do something with data
    console.log(event.data)
  }
</script>
<template>
  <UContainer class="prose">
    <h3>Sample Notes</h3>
    <b>List of names/phone #'s verified by zod schema</b>
    <p>
      Validation: Name should be at least 1 character, number should be a valid
      phone number (based on regex)
    </p>
    <UDivider />
    <UForm
      :schema="phoneListSchema"
      :state="state"
      @submit="onSubmit"
    >
      <table class="table-auto">
        <thead>
          <tr>
            <th>Name</th>
            <th>Number</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="(item, index) in state.items"
            :key="index"
          >
            <td>
              <UFormGroup :name="`items.${index}.name`">
                <UInput
                  v-model="item.name"
                  placeholder="Phone name"
                />
              </UFormGroup>
            </td>
            <td>
              <UFormGroup :name="`items.${index}.number`">
                <UInput
                  v-model="item.number"
                  placeholder="Phone number"
                />
              </UFormGroup>
            </td>
            <td>
              <UButton
                icon="i-heroicons-trash"
                size="sm"
                color="red"
                square
                variant="solid"
                type="button"
                @click="state.items.splice(index, 1)"
              />
            </td>
          </tr>
        </tbody>
        <tfoot>
          <tr>
            <td colspan="2">
              <UButton
                type="button"
                @click="state.items.push({ name: '', number: '' })"
              >
                Add Phone
              </UButton>
            </td>
          </tr>
        </tfoot>
      </table>

      <UButton
        type="submit"
        class="mt-4"
      >
        Save
      </UButton>
    </UForm>
  </UContainer>
</template>
