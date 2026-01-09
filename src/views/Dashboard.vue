<template>
  <div class="flex">
    <Sidebar />

    <div class="flex-1 p-6 bg-gray-100 min-h-screen">
      <h1 class="text-2xl font-bold mb-6">Dashboard</h1>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <div class="bg-white p-4 rounded shadow">
          <h3 class="text-gray-500">Users</h3>
          <p class="text-2xl font-bold">120</p>
        </div>

        <div class="bg-white p-4 rounded shadow">
          <h3 class="text-gray-500">Records</h3>
          <p class="text-2xl font-bold">560</p>
        </div>

        <div class="bg-white p-4 rounded shadow">
          <h3 class="text-gray-500">Status</h3>
          <p class="text-2xl font-bold text-green-600">Active</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import Sidebar from '../components/Sidebar.vue'
</script>
