<template>
  <div>
    <v-container>
      <v-row>
        <v-col cols="12">
          <h3 class="text-center home--first col--presentation--h3">
            Bonjour, je suis Faudel Hadroug
          </h3>
          <br />
          <p class="text-center home--second col--presentation--p">
            Étudiant Web Développeur<i class="btnCall--text">
              aspirant <br />
              à améliorer mes capacités</i
            >.
            <br />
            De naturel <i class="btnCall--text">calme</i> , je suis toujours
            très <i class="btnCall--text">ambitieux</i> quand le sujet me
            passionne (Programmation, Jeux Vidéo, Photographie, Voyage,
            Musique...)
            <br />
            <br />
            <span
              >Recherche une <i class="btnCall--text">alternance</i> pour le
              <br />
              <i class="btnCall--text">02 novembre 2020</i> (12mois)</span
            >
          </p>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="2"></v-col>
        <v-col class="text-center home--cinco" cols="8">
          <NuxtLink to="/contact" tag="main">
            <v-btn
              class="mouseOver"
              :color="colorBtn"
              dark
              large
              width="175px"
              :outlined="!hover"
              :loading="loading"
              @mouseover="hover = true"
              @mouseleave="hover = false"
              @click="loadingComponent"
              >Contactez moi</v-btn
            >
          </NuxtLink>
        </v-col>
        <v-col cols="2"></v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hover: false,
      loading: false,
      visible: true,
    }
  },
  computed: {
    colorBtn() {
      return this.hover ? 'btnCallHover' : 'btnCall'
    },
  },
  methods: {
    loadingComponent() {
      this.loading = !this.loading
      setTimeout(() => {
        // code here
        this.visible = !this.visible
        this.loading = !this.loading
      }, 800)
    },
  },
}
</script>
<style scoped>
.card {
  width: 700px;
}
.mouseOver {
  transition: background-color 0.3s;
}
.col--presentation--h3 {
  font-size: 3vw !important;
}
@media (max-width: 959px) {
  .col--presentation--h3 {
    font-size: 8vw !important;
  }
}

/* text */

.col--presentation--p {
  font-size: 2.2vw;
}
@media (max-width: 959px) {
  .col--presentation--p {
    font-size: 4vw !important;
  }
}
</style>
