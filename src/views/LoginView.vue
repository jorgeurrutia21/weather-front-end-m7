<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-6">
        <div class="card shadow">
          <div class="card-body">
            <h2 class="text-center mb-4">Iniciar Sesión</h2>

            <form @submit.prevent="login">
              <div class="mb-3">
                <label class="form-label"> Correo </label>

                <input
                  v-model="email"
                  type="email"
                  class="form-control"
                  placeholder="correo@ejemplo.com"
                  required
                />
              </div>

              <div class="mb-3">
                <label class="form-label"> Contraseña </label>

                <input
                  v-model="password"
                  type="password"
                  class="form-control"
                  placeholder="********"
                  required
                />
              </div>

              <button type="submit" class="btn btn-primary w-100">Ingresar</button>
            </form>

            <div v-if="error" class="alert alert-danger mt-3">
              {{ error }}
            </div>

            <div class="text-center mt-3">
              <router-link to="/registro" class="link-login">
                ¿No Tienes Cuenta? Regístrate Aquí
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import { signInWithEmailAndPassword } from 'firebase/auth'

import { auth, db } from '@/firebase/config'
import { doc, getDoc } from 'firebase/firestore'

import { useAuthStore } from '@/stores/auth'

const router = useRouter()
const authStore = useAuthStore()

const email = ref('')
const password = ref('')
const error = ref('')

async function login() {
  error.value = ''

  try {
    const credenciales = await signInWithEmailAndPassword(auth, email.value, password.value)

    const ref = doc(db, 'usuarios', credenciales.user.uid) //trae los datos de los usuarios de firestore
    const snap = await getDoc(ref)

    if (snap.exists()) {
      const data = snap.data()

      authStore.setUserData({
        user: {
          uid: credenciales.user.uid,
          email: credenciales.user.email,
        },
        favoritos: data.favoritos || [],
        preferencias: data.preferencias || {
          temperatura: 'Celsius',
        },
      })
    } else {
      authStore.setUser({
        uid: credenciales.user.uid,
        email: credenciales.user.email,
      })
    }

    router.push('/') //redirigue al home
  } catch (err) {
    error.value = 'Usuario o contraseña incorrectos'
    console.error(err)
  }
}
</script>

<style scoped>
.card {
  border-radius: 12px;
  background-color: #6283ae;
}

h2 {
  color: #fcfdff;
}

.link-login {
  color: white;
  text-decoration: none;
  transition: color 0.3s ease;
}

.link-login:hover {
  color: #d4d0d0;
}
</style>
