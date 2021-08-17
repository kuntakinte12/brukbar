<template>
  <v-app>
    <v-app-bar color="white" app elevate-on-scroll>
      <v-container class="d-flex justify-center mt-5">
        <img class="logo" src="~assets/logo/circle.png" alt="" />
        <img class="logo" src="~assets/logo/text_black.png" alt="" />
      </v-container>

      <template v-slot:extension>
        <v-tabs
          flat
          color="grey darken-4"
          class="ml-4 d-none d-sm-flex justify-center"
        >
          <v-tab v-for="(tab, t) in tabs" :key="t">{{ tab.name }}</v-tab>
        </v-tabs>
      </template>

      <v-app-bar-nav-icon
        class="d-flex d-sm-none flex-row-reverse"
        @click="drawer = true"
      ></v-app-bar-nav-icon>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      absolute
      temporary
      right
      color="accent"
    >
      <v-list nav dense>
        <v-list-item-group v-model="group" active-class="text--accent-4">
          <v-list-item
            v-for="(tab, t) in tabs"
            :key="t"
            @click="drawer = false"
          >
            <v-list-item-title>{{ tab.name }}</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container>
        <v-card class="my-4" color="accent">
          <v-carousel>
            <v-carousel-item
              v-for="(item, i) in items"
              :key="i"
              :src="item.src"
              reverse-transition="fade-transition"
              transition="fade-transition"
            ></v-carousel-item>
          </v-carousel>
        </v-card>

        <v-card class="my-4" color="accent">
          <v-card-title>Om oss</v-card-title>
          <v-img
            class="mx-4"
            src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
            height="200px"
          ></v-img>
          <v-card-text
            >Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim
            ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
            aliquip ex ea commodo consequat. Duis aute irure dolor in
            reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla
            pariatur. Excepteur sint occaecat cupidatat non proident, sunt in
            culpa qui officia deserunt mollit anim id est laborum.</v-card-text
          >
        </v-card>

        <v-card class="my-4" color="accent">
          <v-card-title>Kontakt</v-card-title>
          <v-card-text>Adress</v-card-text>
        </v-card>
      </v-container>
    </v-main>

    <v-footer color="grey lighten-2" app>
      <v-container>
        <v-row align="center" justify="center">
          <v-divider class="ma-2" vertical></v-divider>
          <v-icon class="ma-2" large>fas fa-map-marker-alt</v-icon>
          <v-icon class="ma-2" large>fab fa-facebook-square</v-icon>
          <v-icon class="ma-2" large>fab fa-instagram</v-icon>
          <v-divider class="ma-2" vertical></v-divider>
        </v-row>
      </v-container>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          src: '~/assets/images/one.jpg',
        },
        {
          src: './assets/images/two.jpg',
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/bird.jpg',
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/planet.jpg',
        },
      ],
      tabs: [
        {
          name: 'Produkter',
        },
        {
          name: 'Om oss',
        },
        {
          name: 'Kontakt',
        },
      ],
      drawer: false,
      group: null,
    }
  },
}
</script>

<style>
.logo {
  max-height: 100px;
}
div.v-toolbar__extension {
  background-color: #e57373;
  height: 25px !important;
  margin-top: 23px;
}
</style>
