<template>
  <nav class="navbar navbar-expand-lg navbar-dark sticky-top">
    <div class="container-fluid">
      <router-link to="/" class="navbar-brand fw-bold"> 🌤 El Tiempo </router-link>

      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#menuNav"
        aria-controls="menuNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="menuNav">
        <div class="navbar-nav ms-auto align-items-center">
          <router-link to="/" class="nav-link"> Home </router-link>

          <router-link to="/about" class="nav-link"> Nosotros </router-link>

          <router-link v-if="authStore.user" to="/favoritos" class="nav-link">
            Favoritos
          </router-link>

          <router-link v-if="!authStore.user" to="/login" class="nav-link">
            Iniciar Sesión
          </router-link>

          <router-link v-if="!authStore.user" to="/registro" class="nav-link">
            Registrarse
          </router-link>

          <span v-if="authStore.user" class="text-white ms-3 me-3 fw-bold">
            {{ authStore.user.email }}
          </span>

          <button v-if="authStore.user" class="btn btn-outline-light" @click="logout">
            Cerrar Sesión
          </button>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { signOut } from 'firebase/auth'
import { useRouter } from 'vue-router'

import { auth } from '@/firebase/config'

import { useAuthStore } from '@/stores/auth'

const router = useRouter()

const authStore = useAuthStore()

async function logout() {
  try {
    await signOut(auth)

    authStore.clearUser()

    router.push('/login')
  } catch (error) {
    console.error(error)
    alert('Error al cerrar sesión')
  }
}
</script>

<style scoped>
.navbar {
  background-color: #071629;
  color: #ffffff;
  padding: 1rem 0;
}

.nav-link {
  color: white !important;
}

.nav-link:hover {
  color: #87ceeb !important;
}

.btn-outline-light {
  margin-left: 10px;
}
</style>
