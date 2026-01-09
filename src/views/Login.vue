<template>
  <div class="min-h-screen flex items-center justify-center bg-gray-100">
    <div class="bg-white p-6 rounded shadow w-80">
      <h1 class="text-xl font-bold mb-4">Login</h1>

      <input
        v-model="email"
        class="w-full border p-2 mb-3"
        placeholder="Email"
      />

      <input
        v-model="password"
        type="password"
        class="w-full border p-2 mb-4"
        placeholder="Password"
      />

      <button
        @click="login"
        class="w-full bg-blue-600 text-white py-2 rounded"
      >
        Login
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const email = ref('')
const password = ref('')
const router = useRouter()

const login = () => {
  if (!email.value || !password.value) return

  localStorage.setItem('isLoggedIn', 'true')
  router.push('/dashboard')
}
</script>
