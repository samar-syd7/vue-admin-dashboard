<template>
  <table class="w-full border">
    <thead>
      <tr class="bg-gray-200">
        <th class="p-2 text-left">Name</th>
        <th class="p-2 text-left">Email</th>
        <th class="p-2">Actions</th>
      </tr>
    </thead>

    <tbody>
      <tr v-for="user in users" :key="user.id" class="border-t">
        <td class="p-2">{{ user.name }}</td>
        <td class="p-2">{{ user.email }}</td>
        <td class="p-2 text-center space-x-2">
          <button @click="$emit('edit', user)" class="text-blue-600">
            Edit
          </button>
          <button @click="$emit('delete', user.id)" class="text-red-600">
            Delete
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
defineProps({
  users: Array,
})
</script>
