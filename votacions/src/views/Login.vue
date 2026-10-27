<script setup>
import { ref } from 'vue'
import { useAppStore } from '../stores/app.js';
import { useRouter } from 'vue-router'

const email = ref('')
const password = ref('')
const appStore = useAppStore()
const router = useRouter();
function login() {
  if (email.value == "user" && Number(password.value) == 123) {
    appStore.setLoginInfo({
      loggedIn: true,
      username: email.value,
      image: ''
    })
    router.push({name: 'votacions'})
  }
}
</script>

<template>
  <main class="login-page">
    <div class="login-card">
      <h1>Iniciar Sessió</h1>

      <form @submit.prevent="login">
        <label for="user">Usuari</label>
        <input v-model="email" required />

        <label for="password">Password</label>
        <input v-model="password" type="password" required />

        <button type="submit">Entrar</button>
      </form>

    </div>
  </main>
</template>

<style scoped>
.login-page {
  min-height: 100vh;
  display: grid;
  place-items: center;
  background: linear-gradient(135deg, #eef2ff, #f8fafc);
  font-family: Arial, sans-serif;
}

.login-card {
  width: 100%;
  max-width: 380px;
  background: white;
  padding: 2rem;
  border-radius: 18px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
}

h1 {
  margin: 0 0 1.5rem;
  text-align: center;
  color: #1f2937;
}

form {
  display: flex;
  flex-direction: column;
  gap: 0.9rem;
}

label {
  font-size: 0.9rem;
  color: #374151;
  font-weight: 600;
}

input {
  padding: 0.8rem 0.9rem;
  border: 1px solid #d1d5db;
  border-radius: 10px;
  font-size: 1rem;
  outline: none;
}

input:focus {
  border-color: #6366f1;
  box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.15);
}

.options {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 0.85rem;
  margin-top: 0.2rem;
}

.remember {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

a {
  color: #4f46e5;
  text-decoration: none;
}

button {
  margin-top: 0.5rem;
  background: #4f46e5;
  color: white;
  border: none;
  border-radius: 10px;
  padding: 0.9rem;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
}

button:hover {
  background: #4338ca;
}

.register {
  text-align: center;
  margin-top: 1.2rem;
  color: #4b5563;
  font-size: 0.9rem;
}
</style>
