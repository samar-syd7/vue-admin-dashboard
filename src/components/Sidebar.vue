<template>
  <div class="w-60 min-h-screen bg-gray-800 text-white p-4">
    <h2 class="text-xl font-bold mb-6">Admin</h2>

    <nav class="space-y-2">
      <router-link
        to="/dashboard"
        class="block px-3 py-2 rounded hover:bg-gray-700"
      >
        Dashboard
      </router-link>

      <router-link
        to="/users"
        class="block px-3 py-2 rounded hover:bg-gray-700"
      >
        Users
      </router-link>
    </nav>
  </div>
</template>
