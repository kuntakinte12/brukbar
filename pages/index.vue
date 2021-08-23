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
          <v-tab
            v-for="(tab, t) in tabs"
            :key="t"
            @click="$vuetify.goTo(tab.src, options)"
            >{{ tab.name }}</v-tab
          >
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
            @click="
              drawer = false
              $vuetify.goTo(tab.src)
            "
          >
            <v-list-item-title>{{ tab.name }}</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container>
        <v-card class="my-4" color="accent" id="produkter">
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

        <v-card class="my-4" color="accent" id="om">
          <v-card-title>Om oss</v-card-title>
          <v-img class="mx-4" :src="store_src" height="200px"></v-img>
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

        <v-card class="my-4" color="accent" id="kontakt">
          <v-card-title>Kontakt</v-card-title>
          <v-row class="d-flex flex-row mx-4 mb-2">
            <div>
              <span class="thick">Address</span><br />
              <address>
                Sandgatan 479 <br />
                740 35 <br />
                Enköping
              </address>
            </div>
            <div></div>
          </v-row>

          <Map class="ma-4" />
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
          src: require('../assets/images/one.jpg'),
        },
        {
          src: require('../assets/images/two.jpg'),
        },
        {
          src: require('../assets/images/three.jpg'),
        },
        {
          src: require('../assets/images/four.jpg'),
        },
      ],
      tabs: [
        {
          name: 'Produkter',
          src: '#produkter',
        },
        {
          name: 'Om oss',
          src: '#om',
        },
        {
          name: 'Kontakt',
          src: '#kontakt',
        },
      ],
      drawer: false,
      group: null,
      store_src: require('../assets/images/store.jpg'),
      options: {
        duration: 300,
        offset: 30,
        easing: 'easeInCubic',
      },
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
span.thick {
  font-weight: bold;
}
</style>
