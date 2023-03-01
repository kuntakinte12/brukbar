<template>
  <v-app>
    <div class="header header-shadow">
      <v-row class="d-flex justify-center">
        <img class="logo header-margin" src="~assets/logo/circle.png" alt="" />
        <img
          class="logo header-margin"
          src="~assets/logo/text_black.png"
          alt=""
        />
      </v-row>
      <v-card class="d-flex justify-center" color="#f5f3ef" flat tile>
        <v-card
          v-for="(tab, t) in tabs"
          :key="t"
          @click="$vuetify.goTo(tab.src, options)"
          class="px-2 pt-1"
          outlined
          tile
          color="#f5f3ef"
          height="35px"
        >
          {{ tab.name }}
        </v-card>
      </v-card>
    </div>

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
            ><p class="font-weight-medium">
              Är du en hemmafixare som gillar att använda ordentliga brukbara
              något äldre verktyg?
            </p>
            <p class="font-weight-medium">
              Kom in i butiken och kolla våra priser för begagnade verktyg,
              elverktyg, specialverktyg, spik & skruv, husgeråd, belysning, vvs,
              trädgårdsredskap m.m.
            </p>
            <p class="font-weight-medium">
              Har du begagnade och brukbara saker hemma som du vill bli av med?
              Kontakta oss gärna, du kan även lämna i eller utanför butiken. Vi
              kan även hämta hos Dig (inom kommunen).
            </p>
            <p class="font-weight-bold text-decoration-underline">
              Ny address är Sämskarbogatan 8. Infart från Salavägen mittemot
              Willys.
            </p></v-card-text
          >
        </v-card>

        <v-card class="my-4 pb-1" color="accent" id="kontakt">
          <v-card-title>Kontakt</v-card-title>

          <v-row class="d-flex flex-row mx-4 mb-2">
            <div class="mr-10">
              <span class="thick">Address</span><br />
              <a href="https://goo.gl/maps/NguWL6DicbRTkH5S8" target="_blank">
                Sämskarbogatan 8 <br />
                745 33 <br />
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
            href="https://goo.gl/maps/9DiYsjSY7LGLDyf88"
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
            <v-icon class="ma-2" large color="#E56969">fab fa-instagram</v-icon>
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
        {
          src: require('../assets/images/five.jpg'),
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
        offset: 140,
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
span.thick {
  font-weight: bold;
}
a.a-icon {
  color: #f2f2f2 !important;
}
.header-shadow {
  box-shadow: 0px 1px 6px gray;
}
.header {
  background-color: #f5f3ef;
  position: sticky;
  top: 0;
  z-index: 1000;
}
.header-margin {
  margin-top: 8px;
}
</style>
