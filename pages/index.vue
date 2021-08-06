<template>
  <v-app>
    <v-app-bar app dense>
      <v-tabs align-with-title>
        <v-tab>Om oss</v-tab>
        <v-tab>Produkter</v-tab>
        <v-tab>Kontakt</v-tab>
      </v-tabs>
    </v-app-bar>

    <v-main>
      <v-container fluid>
        <router-view></router-view>
      </v-container>
    </v-main>

    <v-footer app>
      <v-container>
        <v-row align="center" justify="center">
          <v-icon large>fas fa-map-marker-alt</v-icon>
          <v-icon class="ma-4" large>fab fa-facebook-square</v-icon>
          <v-icon large>fab fa-instagram</v-icon>
        </v-row>
      </v-container>
    </v-footer>
  </v-app>
</template>

<script>
export default {}
</script>

<style></style>
