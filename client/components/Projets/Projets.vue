<template>
  <v-container>
    <v-row justify="space-around">
      <v-col cols="0" md="4"></v-col>
      <v-col cols="12" md="4">
        <div class="display-2 text-center">{{ slides[model].name }}</div>
      </v-col>
      <v-col cols="0" md="4"></v-col>
    </v-row>

    <v-row>
      <v-col cols="12">
        <v-carousel v-model="model" show-arrows-on-hover>
          <v-carousel-item
            v-for="(slide, i) in slides"
            :key="i"
            class="responsive--img"
            :src="slide.image"
            :href="slide.link"
            target="_blank"
          >
          </v-carousel-item>
        </v-carousel>
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="1"></v-col>
      <v-col cols="12" md="5">
        <div>
          <p>{{ slides[model].description }}</p>
        </div>
      </v-col>
      <v-col cols="1"></v-col>
      <v-col cols="12" md="4">
        <div>
          <p>{{ slides[model].duree }}</p>
        </div>
        <div>
          <p></p>
        </div>
      </v-col>
      <v-col cols="1"></v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      model: 0,
      colors: ['indigo', 'warning', 'pink darken-2', 'red lighten-1'],
      slides: [
        {
          name: 'E-commerce',
          image: require('@/assets/projets/e-commerce.png'),
          description:
            "Site de vente de vêtement haut de gamme 'blueprint', avec un maximum de fonctionnalités. En groupe de 8 en utilisant la méthodologie Agile via Gitlab. mise en place d'un pannel admin, connexion api, compte utilisateur, authentification redux...",
          duree: 'Réalisé en 1 mois, du 1/6/20 au 30/6/20',
          link: 'https://e-8commerce-client.herokuapp.com/',
        },
        {
          name: 'Twitter',
          image: require('@/assets/projets/twitter.png'),
          description:
            'Le but de ce projet est de créer un réseau social pour les étudiants de notre promotion, qui aura les mêmes fonctionnalités que twitter.Il devra être le plus ressemblant possible en terme de fonctionnalités par rapport au site Twitter. Noté 42/20 (meilleure note possible pour un projet).',
          duree: 'Réalisé en 2 semaines, du 17/2/20 au 1/4/20',
          link: 'https://tweet-academie-42.herokuapp.com/',
        },
        {
          name: 'My_irc',
          image: require('@/assets/projets/my-irc.png'),
          description:
            'Réalisation d’un IRC, découverte de socket io. Implémentation d’un serveur à connexions simultanées avec plusieurs “channels” ainsi que des fonctionnalités cachées via des lignes de commandes',
          duree: 'Réalisé en 2 semaines, du 11/5/20 au 24/5/20',
          link: '',
        },
        {
          name: 'My_quizz',
          image: require('@/assets/projets/my-quizz.png'),
          description:
            "Site qui permet de tester sa culture générale à travers des quiz. Les utilisateurs peuvent créer leur propres quiz et jouer aux quiz des autres utilisateurs. Système d'historique par utilisateur et possibilité de jouer en anonyme.",
          duree: 'Réalisé en 2 semaines, du 20/4/20 au 3/5/20',
          link: '',
        },
      ],
    }
  },
  head: {
    title: 'Projets',
    meta: [
      {
        hid:
          'Aperçu de quelques projets réalisés au cours de ma formation au Samsung Campus',
        name: 'description',
        content: process.env.npm_package_description || '',
      },
    ],
  },
}
</script>

<style lang="scss" scoped>
.responsive--img {
  width: 100%;
  height: auto;
}
</style>
