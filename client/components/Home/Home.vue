<template>
  <div>
    <!-- <div class="dev">{{ typeDevice }}</div> -->
    <v-container>
      <v-row>
        <v-col id="col--presentation" cols="12" md="6">
          <Presentation />
        </v-col>
        <v-col id="col--preference" cols="12" md="4">
          <Preference />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      errorAlertDevice: false,
      first: 'first',
      typeDevice: '',
    }
  },
  created() {
    addEventListener('resize', this.myEventHandler)
    this.typeDevice = this.$vuetify.breakpoint.name
  },

  destroyed() {
    window.removeEventListener('resize', this.myEventHandler)
  },
  methods: {
    myEventHandler(e) {
      if (this.typeDevice !== this.$vuetify.breakpoint.name) {
        // alert('changement device')
        this.typeDevice = this.$vuetify.breakpoint.name
      }
    },
  },
  head: {
    title: 'Home',
    meta: [
      {
        hid: 'home page de mon portfolio',
        name: 'description',
        content: process.env.npm_package_description || '',
      },
    ],
  },
}
</script>

<style scoped>
.dev {
  color: yellow;
  position: absolute;
  margin-left: 85%;
  z-index: 999;
  font-size: 50px;
}

#col--preference {
  font-size: 3vw;
}
@media (max-width: 959px) {
  #col--preference {
    font-size: 8vw !important;
  }
}
@media (min-width: 960px) {
  #col--presentation {
    margin-top: 10%;
    margin-bottom: 10%;
  }
  #col--preference {
    margin-top: 10%;
    margin-bottom: 10%;
  }
}

@media (min-width: 1264px) {
  #col--presentation {
    margin-top: 5%;
    margin-bottom: 5%;
  }
  #col--preference {
    margin-top: 5%;
    margin-bottom: 5%;
  }
}
</style>
