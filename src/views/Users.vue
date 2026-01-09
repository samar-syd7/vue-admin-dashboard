<template>
  <div class="flex">
    <Sidebar />

    <div class="flex-1 p-6">
      <div class="flex justify-between mb-4">
        <h1 class="text-2xl font-bold">Users</h1>
        <button
          @click="openAdd"
          class="bg-blue-600 text-white px-4 py-2 rounded"
        >
          Add User
        </button>
      </div>

      <!-- Loading state -->
      <div v-if="loading" class="text-gray-600">
        Loading users...
      </div>

      <!-- Error state -->
      <div v-else-if="error" class="text-red-600">
        {{ error }}
      </div>

      <!-- Data table -->
      <DataTable
        v-else
        :users="users"
        @edit="openEdit"
        @delete="removeUser"
      />

      <UserForm
        v-if="showForm"
        :user="selectedUser"
        @save="saveUser"
        @close="closeForm"
      />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import Sidebar from '../components/Sidebar.vue'
import DataTable from '../components/DataTable.vue'
import UserForm from '../components/UserForm.vue'
import { fetchUsers } from '../services/api'

const users = ref([])
const loading = ref(true)
const error = ref(null)

const showForm = ref(false)
const selectedUser = ref(null)

onMounted(async () => {
  try {
    const res = await fetchUsers()
    users.value = res.data
  } catch (err) {
    error.value = 'Failed to load users'
  } finally {
    loading.value = false
  }
})

const openAdd = () => {
  selectedUser.value = null
  showForm.value = true
}

const openEdit = (user) => {
  selectedUser.value = user
  showForm.value = true
}

const saveUser = (user) => {
  if (user.id) {
    const index = users.value.findIndex(u => u.id === user.id)
    users.value[index] = user
  } else {
    user.id = Date.now()
    users.value.push(user)
  }
  closeForm()
}

const removeUser = (id) => {
  users.value = users.value.filter(u => u.id !== id)
}

const closeForm = () => {
  showForm.value = false
}
</script>
