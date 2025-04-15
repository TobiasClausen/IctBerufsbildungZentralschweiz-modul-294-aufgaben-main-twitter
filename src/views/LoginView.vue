<script setup>
import { ref, computed } from 'vue'
import { useRouter } from 'vue-router'
import { loginUser } from '../api/requests'

const router = useRouter()
const email = ref('')
const password = ref('')
const error = ref(null)
const isButtonDisabled = computed(() => !email.value || !password.value)

async function login() {
  error.value = null
  try {
    await loginUser(email.value, password.value)
    router.push('/')
  } catch (err) {
    error.value = err.message || 'Login failed'
    console.error('Login error:', err)
  }
}
</script>

<template>
  <div class="login">
    <section class="login-wrapper">
      <form action="#" class="login-form" autocomplete="off" novalidate @submit.prevent="login">
        <div class="form-group">
          <label class="form-label" for="email">E-Mail</label>
          <input 
            v-model="email"
            class="form-input" 
            type="email" 
            id="email" 
          />
          <div v-if="error" class="form-error">
            {{ error }}
          </div>
        </div>
        <div class="form-group">
          <label class="form-label" for="password">Passwort</label>
          <input 
            v-model="password"
            class="form-input" 
            type="password" 
            id="password" 
          />
        </div>
        <div class="form-group">
          <button 
            :disabled="isButtonDisabled" 
            class="btn btn--primary btn--block"
          >
            Login
          </button>
        </div>
      </form>
    </section>
  </div>
</template>

