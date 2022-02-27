<template>
  <v-app dark>
    <v-app-bar fixed app>
      <v-container class="red mx-auto">
        <v-toolbar-title>Trustpaddi</v-toolbar-title>
      </v-container>
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer :absolute="false" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",
};
</script>
