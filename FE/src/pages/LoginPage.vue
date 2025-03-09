<template>
  <q-page padding>
    <h4>LoginPage</h4>
    <div class="row">
      <div class="col">
        <q-input
          rounded
          outlined
          v-model="eamil"
          suffix="@gmail.com"
          type="email"
          label="Enter Email"
        />
      </div>
      <div class="col">
        <q-input
          rounded
          outlined
          v-model="password"
          :type="isPwd ? 'password' : 'text'"
          label="Enter Password"
          ><template v-slot:append>
            <q-icon
              :type="isPwd ? 'password' : 'text'"
              :name="isPwd ? 'visibility_off' : 'visibility'"
              class="cursor-pointer"
              @click="isPwd = !isPwd"
            /> </template
        ></q-input>
      </div>
    </div>
    <q-btn
      color="amber-9"
      class="full-width q-ma-lg"
      rounded
      glossy
      label="Login"
      @click="login"
    />
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
import { api } from 'src/boot/axios'
import { Notify } from 'quasar'

import { useRouter } from 'vue-router'

const router = useRouter()
const isPwd = ref('true')
const eamil = ref('')
const password = ref('')
function login() {
  api
    .post('/oauth/token', {
      grant_type: 'password',
      client_id: 2,
      client_secret: 'cZKMktjoyfhE8btRncCYw8ODtJ4CDcprJcA3epya',
      username: eamil.value,
      password: password.value,
      scope: '*',
    })
    .then((r) => {
      if (r.data.access_token) {
        localStorage.setItem('access_token', r.data.access_token)
        api.defaults.headers = {
          Authorization: 'Bearer ' + localStorage.getItem('access_token'),
          'Content-Type': 'application/json',
          Accept: 'application/json;charset=UTF-8',
        }
        Notify.create({
          type: 'positive',
          message: 'user login success',
        })
          router.push('/profile')
      }
    })
    .catch((e) => {
      Notify.create({
        type: 'negative',
        message: e.message,
      })
    })
}
</script>
