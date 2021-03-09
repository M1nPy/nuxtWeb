<template>
  <div class="tech-wrap">
    <v-container>
      <v-row>
        <v-card class="flex">
          <v-card-title
            ><h3 class="history-wrap__header--title">使用している技術</h3>
            <v-spacer></v-spacer>
          </v-card-title>
        </v-card>
      </v-row>
      <v-row class="py-4">
        <v-spacer></v-spacer>
        <v-col cols="10">
          <v-card width="100%"
            ><v-container fluid>
              <v-row class="py-2">
                <v-col v-for="item in items" :key="item.name">
                  <v-card
                    class="mx-auto"
                    :max-width="iconheight"
                    @click="selectItem = item.name"
                    ><v-img :src="item.src" aspect-ratio="1"></v-img
                  ></v-card>
                </v-col> </v-row
              ><v-row
                ><v-container>
                  <v-row>
                    <v-col cols="6"
                      ><v-card flat height="600px"
                        ><v-card-title>{{
                          items[selectItem].name
                        }}</v-card-title
                        ><v-card-text>{{
                          items[selectItem].name
                        }}</v-card-text></v-card
                      ></v-col
                    >
                    <v-col align-self="center" cols="6"
                      ><v-img :src="items[selectItem].src"></v-img
                    ></v-col>
                  </v-row> </v-container></v-row></v-container
          ></v-card>
        </v-col>
        <v-spacer></v-spacer>
      </v-row>
    </v-container>
  </div>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'Tech',
  data() {
    return {
      items: {
        nuxt: {
          name: 'nuxt',
          src: require('@/assets/techicons/nuxt-icon.svg'),
        },
        vue: {
          name: 'vue',
          src: require('@/assets/techicons/vue.svg'),
        },
        vuetify: {
          name: 'vuetify',
          src: require('@/assets/techicons/vuetifyjs.svg'),
        },
        typescript: {
          name: 'typescript',
          src: require('@/assets/techicons/typescript-icon.svg'),
        },
        Vuetify: {
          name: 'Vuetify',
          src: require('@/assets/techicons/html-5.svg'),
        },
        css3: {
          name: 'css3',
          src: require('@/assets/techicons/css-3.svg'),
        },
        sass: {
          name: 'sass',
          src: require('@/assets/techicons/sass.svg'),
        },
        javascript: {
          name: 'javascript',
          src: require('@/assets/techicons/javascript.svg'),
        },
        nodejs: {
          name: 'nodejs',
          src: require('@/assets/techicons/nodejs.svg'),
        },
        contentful: {
          name: 'contentful',
          src: require('@/assets/techicons/contentful.svg'),
        },
        sentry: {
          name: 'sentry',
          src: require('@/assets/techicons/sentry-icon.svg'),
        },
        netlify: {
          name: 'netlify',
          src: require('@/assets/techicons/netlify.svg'),
        },
      },
      selectItem: 'vue',
    }
  },
  computed: {
    iconheight() {
      switch (this.$vuetify.breakpoint.name) {
        case 'xs':
          return 40
        case 'sm':
          return 50
        case 'md':
          return 40
        case 'lg':
          return 80
        case 'xl':
          return 90
        default:
          return 0
      }
    },
  },
})
</script>
