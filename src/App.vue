<template>
  <LoginPage
    ref="loginRef"
    brand-name="YourBrand"
    title="Kube-Vue-Admin，欢迎你!"
    subtitle="Please enter your details"
    primary-color="#4f46e5"
    @submit="handleLogin"
  />
</template>

<script setup lang="ts">
import { ref } from 'vue'
import LoginPage from './components/LoginPage.vue'

const loginRef = ref<InstanceType<typeof LoginPage>>()

async function handleLogin(payload: { email: string; password: string; remember: boolean }) {
  loginRef.value?.setLoading(true)

  // Replace with your real auth logic
  await new Promise(r => setTimeout(r, 500))

  if (payload.email === 'demo@example.com' && payload.password === '1234') {
    alert('Login successful!')
  } else {
    loginRef.value?.setError('Invalid email or password.')
  }

  loginRef.value?.setLoading(false)
}
</script>
