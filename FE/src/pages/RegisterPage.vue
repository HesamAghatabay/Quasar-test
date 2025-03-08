<template>
  <q-page padding>
    <h4>RegisterPage</h4>
    <div class="row">
      <div class="col">
        <q-input rounded outlined v-model="name" type="text" label="Enter Name" />
      </div>
      <div class="col">
        <q-input
          rounded
          outlined
          v-model="email"
          type="email"
          label="Enter Email"
          suffix="@gmail.com"
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
              :name="isPwd ? 'visibility_off' : 'visibility'"
              class="cursor-pointer"
              @click="isPwd = !isPwd"
            /> </template
        ></q-input>
      </div>
      <div class="col">
        <q-input
          rounded
          outlined
          v-model="confirm"
          :type="isPwdconfirm ? 'password' : 'text'"
          label="Confirm Password"
          ><template v-slot:append>
            <q-icon
              :name="isPwdconfirm ? 'visibility_off' : 'visibility'"
              class="cursor-pointer"
              @click="isPwdconfirm = !isPwdconfirm"
            /> </template
        ></q-input>
      </div>
    </div>
    <q-btn
      color="amber-9"
      class="full-width q-ma-lg"
      rounded
      glossy
      label="Register"
      @click="register"
    />
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import { Notify } from 'quasar'
import { api } from 'src/boot/axios'


const name = ref('')
const email = ref('')
const password = ref('')
const confirm = ref('')
const isPwd = ref(true)
const isPwdconfirm = ref(true)
const router = useRouter()


function register() {
  if(password.value === confirm.value){
    api.post('/api/register',{
      name : name.value,
      email : email.value,
      password : password.value,
    }).then(()=>{
      Notify.create({
            type: 'positive',
            message: 'user register success',
          })
          router.push('/login')
    })
  }
}

</script>