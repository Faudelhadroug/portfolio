<template>
  <div id="navBar">
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      :disable-resize-watcher="true"
      fixed
      app
    >
      <v-list>
        <v-icon class="ml-4 mb-2" @click="drawer = !drawer">
          mdi-close-box
        </v-icon>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon
        class="d-md-none d-lg-none"
        @click.stop="drawer = !drawer"
      />
      <v-btn
        v-for="(item, i) in items"
        :key="i"
        text
        rounded
        :to="item.to"
        class="d-none d-md-block"
        router
        exact
      >
        <v-icon class="mt-1">{{ item.title }}</v-icon></v-btn
      >
      <v-spacer></v-spacer>
      <v-btn class="mr-5" @click="toggleTheme">
        {{ darkmode ? 'Light mode' : 'Dark mode' }}
      </v-btn>
      <v-toolbar-title class="subtitle-2 float-right" v-text="title" />
    </v-app-bar>
  </div>
</template>

<script>
export default {
  data() {
    return {
      clipped: true, // ne pas toucher permet de laissé la navbar en dessous
      drawer: false, // ouvre le menu
      fixed: false, // ? Cache le footer si true quand il y a du contenu sur la page
      items: [
        {
          icon: 'mdi-home-assistant',
          title: 'Accueil',
          to: '/',
        },
        {
          icon: 'mdi-dev-to',
          title: 'Projets',
          to: '/projets',
        },
        {
          icon: 'mdi-card-account-mail',
          title: 'Contact',
          to: '/contact',
        },
      ],
      miniVariant: false, // false permet dafficher la nav du côté en entier
      title: 'Faudel HADROUG',
      darkmode: true,
    }
  },
  methods: {
    toggleTheme() {
      this.darkmode = !this.darkmode
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark
    },
  },
}
</script>

<style lang="scss" scoped>
#navBar {
  margin-bottom: 60px;
}
</style>
