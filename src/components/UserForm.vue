<template>
  <div class="fixed inset-0 bg-black bg-opacity-40 flex items-center justify-center">
    <div class="bg-white p-6 rounded w-96">
      <h2 class="text-lg font-bold mb-4">
        {{ user ? 'Edit User' : 'Add User' }}
      </h2>

      <input
        v-model="form.name"
        placeholder="Name"
        class="w-full border p-2 mb-3"
      />

      <input
        v-model="form.email"
        placeholder="Email"
        class="w-full border p-2 mb-4"
      />

      <div class="flex justify-end gap-2">
        <button @click="$emit('close')" class="px-4 py-2 border">
          Cancel
        </button>
        <button @click="submit" class="px-4 py-2 bg-blue-600 text-white">
          Save
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive, watch } from 'vue'

const props = defineProps({
  user: Object,
})

const emit = defineEmits(['save', 'close'])

const form = reactive({
  name: '',
  email: '',
})

watch(
  () => props.user,
  (val) => {
    if (val) {
      form.name = val.name
      form.email = val.email
    }
  },
  { immediate: true }
)

const submit = () => {
  emit('save', { ...props.user, ...form })
}
</script>
