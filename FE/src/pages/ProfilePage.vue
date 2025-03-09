<template>
  <q-page padding>
    <h4>ProfilPage</h4>

    <q-inner-loading size="25px" label="please wait" />
    <div v-if="!user">
      <p>{{ user.profile.full_name }}</p>
    </div>
  </q-page>
</template>

<script setup>
//
</script>
