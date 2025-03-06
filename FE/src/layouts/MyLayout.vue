<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated>
      <q-toolbar class="bg-purple-10 glossy text-white q-px-lg">
        <q-toolbar-title>
          <q-btn color="amber-10" rounded glossy icon="home" to="/" />
          WELCOME
        </q-toolbar-title>
        <q-btn-group rounded>
          <q-btn color="amber-10" rounded glossy label="Register" to="/register" />
          <q-btn color="amber-10" rounded glossy label="Login" to="/login" />
          <q-btn color="amber-10" rounded glossy label="Profile" to="/profile" />
        </q-btn-group>
      </q-toolbar>
    </q-header>

    <!-- <q-drawer v-model="leftDrawerOpen" side="left" elevated>
      <q-btn-group>
        <q-btn color="amber" glossy label="First" />
        <q-btn color="amber" glossy label="Second" />
        <q-btn color="amber" glossy label="Third" />
        <q-btn color="amber" glossy label="Fourth" />
      </q-btn-group>
    </q-drawer> -->

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer elevated class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg" />
          </q-avatar>
          <div>Title</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
// import { ref } from 'vue'

// export default {
//   setup() {
//     const leftDrawerOpen = ref(false)

//     return {
//       leftDrawerOpen,
//       toggleLeftDrawer() {
//         leftDrawerOpen.value = !leftDrawerOpen.value
//       },
//     }
//   },
// }
</script>