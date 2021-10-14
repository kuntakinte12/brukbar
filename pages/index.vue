<template>
  <v-app>
    <v-app-bar color="#f5f3ef" app elevate-on-scroll>
      <v-container class="d-flex justify-center mt-6">
        <img class="logo" src="~assets/logo/circle.png" alt="" />
        <img class="logo" src="~assets/logo/text_black.png" alt="" />
      </v-container>

      <template v-slot:extension>
        <v-tabs
          flat
          color="grey darken-4"
          class="ml-4 d-sm-flex justify-center"
        >
          <v-tab
            v-for="(tab, t) in tabs"
            :key="t"
            @click="$vuetify.goTo(tab.src, options)"
            >{{ tab.name }}</v-tab
          >
        </v-tabs>
      </template>
    </v-app-bar>

    <v-main>
      <v-container color="#f5f3ef">
        <v-card class="my-4" color="accent" id="start">
          <v-carousel
            v-model="activeSlide"
            :touch="{
              left: () => activeSlide--,
              right: () => activeSlide++,
            }"
          >
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

        <v-card class="my-4 pb-1" color="accent" id="kontakt">
          <v-card-title>Kontakt</v-card-title>

          <v-row class="d-flex flex-row mx-4 mb-2">
            <div class="mr-10">
              <span class="thick">Address</span><br />
              <a href="https://goo.gl/maps/jWJW6aofxKJmnAzP7" target="_blank">
                Kvartsgatan 1C <br />
                749 40 <br />
                Enköping
              </a>
            </div>
            <div class="mr-10">
              <span class="thick">Kontaktinformation</span><br />
              Telefon: <a href="tel:0708955920">070-895 59 20</a><br />
              Swish: <a href="tel:1233667581">123-366 7581</a><br />
              Mail: <a href="mailto:brukbar@brukbar.nu">brukbar@brukbar.nu</a>
            </div>
            <div class="mr-10">
              <span class="thick">Öppettider</span><br />
              Torsdagar: 13.00 - 17.00 <br />
              Fredagar: 13.00 - 17.00 <br />
              Lördagar: 10.00 - 14.00<br />
            </div>
          </v-row>

          <Map class="ma-4" />
        </v-card>
      </v-container>
    </v-main>

    <v-footer color="accent" app>
      <v-container>
        <v-row align="center" justify="center">
          <v-divider class="ma-2" vertical></v-divider>
          <a
            class="a-icon"
            href="https://goo.gl/maps/jWJW6aofxKJmnAzP7"
            target="_blank"
          >
            <v-icon class="ma-2" large color="#DD0612"
              >fas fa-map-marker-alt</v-icon
            >
          </a>
          <a
            class="a-icon"
            href="https://www.facebook.com/profile.php?id=100070918456870"
            target="_blank"
          >
            <v-icon class="ma-2" large color="#4267B2"
              >fab fa-facebook-square</v-icon
            >
          </a>
          <a
            class="a-icon"
            href="https://www.instagram.com/brukbarab/"
            target="_blank"
          >
            <v-icon class="ma-2 fa-instagram" large
              >fab fa-instagram-square</v-icon
            >
          </a>
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
      activeSlide: 0,
      tabs: [
        {
          name: 'Start',
          src: '#start',
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
        offset: 10,
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
  background-color: #f5f3ef;
  height: 25px !important;
  margin-top: 23px;
}
span.thick {
  font-weight: bold;
}
a.a-icon {
  color: #f2f2f2 !important;
}
.fa-instagram {
  font-size: 30px;
  background: #d6249f;
  background: radial-gradient(
    circle at 30% 107%,
    #fdf497 0%,
    #fdf497 5%,
    #fd5949 45%,
    #d6249f 60%,
    #285aeb 90%
  );
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
</style>
