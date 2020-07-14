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
      <v-col cols="2" sm="3"></v-col>
      <v-col cols="8" sm="6">
        <v-alert v-show="info" type="info">
          Il est possible d'accéder au projet avec un click sur l'image quand
          celui-ci est héberger en ligne.
        </v-alert>
      </v-col>
      <v-col cols="2" sm="3"></v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <v-carousel v-model="model" show-arrows-on-hover>
          <v-carousel-item
            v-for="(slide, i) in slides"
            :key="i"
            height="auto"
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
          <a
            v-if="slides[model].awardLink"
            :href="slides[model].awardLink"
            target="_blank"
          >
            <p class="btnCall--text">{{ slides[model].award }}</p>
          </a>
          <p v-else class="btnCall--text">{{ slides[model].award }}</p>
        </div>
      </v-col>
      <v-col cols="1"></v-col>
      <v-col cols="12" md="4">
        <div>
          <p class="text-center">{{ slides[model].duree }}</p>
        </div>
        <v-row justify="center">
          <span v-for="techno in slides[model].technos" :key="techno">
            <v-img width="64px" class="responsive--img" :src="techno" />
          </span>
        </v-row>
        <div class="mt-10">
          <a :href="slides[model].github" target="_blank">
            <p class="text-center">Github du projet</p>
          </a>
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
      info: true,
      model: 0,
      slides: [
        {
          name: 'E-commerce',
          image: require('@/assets/projets/e-commerce.png'),
          description:
            "Site de vente de vêtement haut de gamme 'blueprint', avec un maximum de fonctionnalités. En groupe de 8 en utilisant la méthodologie Agile via Gitlab. mise en place d'un pannel admin, connexion api, compte utilisateur, authentification redux...",
          award: 'Victoire Marketing décernée par l’ESSEC Business School',
          duree: 'Groupe de 8. Réalisé en 1 mois, du 1/6/20 au 30/6/20',
          link: 'https://e-8commerce-client.herokuapp.com/',
          technos: [
            require('@/assets/logoTechno/react.svg'),
            require('@/assets/logoTechno/redux.svg'),
            require('@/assets/logoTechno/symfony.svg'),
            require('@/assets/logoTechno/bootstrap.png'),
          ],
          github: 'https://github.com/reyesvictor/8-commerce',
          awardLink:
            'https://www.linkedin.com/feed/update/urn:li:activity:6685934491401256960/',
        },
        {
          name: 'Twitter',
          image: require('@/assets/projets/twitter.png'),
          description:
            'Le but de ce projet est de créer un réseau social pour les étudiants de notre promotion, qui aura les mêmes fonctionnalités que twitter.Il devra être le plus ressemblant possible en terme de fonctionnalités par rapport au site Twitter. Noté 42/20 (meilleure note possible pour un projet).',
          award: 'Noté 42/20 (meilleure note possible pour un projet).',
          duree: 'Groupe de 4. Réalisé en 2 semaines, du 17/2/20 au 1/4/20',
          link: 'https://tweet-academie-42.herokuapp.com/',
          technos: [
            require('@/assets/logoTechno/jquery.png'),
            require('@/assets/logoTechno/php.png'),
          ],
          github: 'https://github.com/reyesvictor/Tweet_Academie_Public/',
        },
        {
          name: 'My_irc',
          image: require('@/assets/projets/my-irc.png'),
          description:
            'Réalisation d’un IRC, découverte de socket io. Implémentation d’un serveur à connexions simultanées avec plusieurs “channels” ainsi que des fonctionnalités cachées via des lignes de commandes',
          duree: 'Réalisé seul en 2 semaines, du 11/5/20 au 24/5/20',
          link: '',
          technos: [
            require('@/assets/logoTechno/react.svg'),
            require('@/assets/logoTechno/nodejs.svg'),
            require('@/assets/logoTechno/expressjs.png'),
            require('@/assets/logoTechno/socketio.png'),
          ],
          github: 'https://github.com/Faudelhadroug/my_irc',
        },
        {
          name: 'My_quizz',
          image: require('@/assets/projets/my-quizz.png'),
          description:
            "Site qui permet de tester sa culture générale à travers des quiz. Les utilisateurs peuvent créer leur propres quiz et jouer aux quiz des autres utilisateurs. Système d'historique par utilisateur et possibilité de jouer en anonyme.",
          duree: 'Réalisé seul en 2 semaines, du 20/4/20 au 3/5/20',
          link: '',
          technos: [require('@/assets/logoTechno/symfony.svg')],
          github: 'https://github.com/Faudelhadroug/MVC_My_Quiz_Public',
        },
        {
          name: 'My_Snapchat',
          image: require('@/assets/projets/my_snapchat.png'),
          description:
            "Reproduction des fonctionnalités de Snapchat en utilisant l'API fournie par Epitech. L'application envoie des images à vos amis pour un laps de temps, et seront supprimés par la suite.",
          duree: 'Groupe de 2. Réalisé en 1 semaine, du 25/5/20 au 31/5/20',
          link: 'http://snap-nf.surge.sh/',
          technos: [require('@/assets/logoTechno/react.svg')],
          github: 'https://github.com/Elbarkaoui-Nordine/my_snapchat',
        },
      ],
    }
  },
  mounted() {
    setTimeout(() => {
      this.info = this.info = false
    }, 7500)
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

<style lang="scss" scoped></style>
