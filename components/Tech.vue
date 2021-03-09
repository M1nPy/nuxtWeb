<template>
  <div class="tech-wrap">
    <v-container>
      <v-row>
        <v-card class="flex">
          <v-card-title
            ><h3 class="history-wrap__header--title">
              Such as frameworks used on this site
            </h3>
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
                    ><v-img
                      :contain="true"
                      :src="item.src"
                      aspect-ratio="1"
                    ></v-img
                  ></v-card>
                </v-col> </v-row
              ><v-row
                ><v-container>
                  <v-row>
                    <v-col cols="6"
                      ><v-card flat height="500px" class="py-10"
                        ><v-card-title>{{
                          items[selectItem].name
                        }}</v-card-title
                        ><v-card-text>{{
                          items[selectItem].text
                        }}</v-card-text></v-card
                      ></v-col
                    >
                    <v-col align-self="center" cols="6">
                      <v-img
                        max-height="300px"
                        :contain="true"
                        :src="items[selectItem].src"
                        ><a
                          target="_blank"
                          rel="noopener noreferrer"
                          class="tech-wrap__view--img-a"
                          :href="items[selectItem].homepage"
                        ></a
                      ></v-img>
                    </v-col>
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
        Nuxt: {
          name: 'Nuxt',
          src: require('@/assets/techicons/nuxt-icon.svg'),
          text: 'The Intuitive Vue Framework',
          homepage: 'https://nuxtjs.org/',
        },
        Vue: {
          name: 'Vue',
          src: require('@/assets/techicons/vue.svg'),
          text: 'The Progressive JavaScript framework.',
          homepage: 'https://vuejs.org/index.html',
        },
        Vuetify: {
          name: 'Vuetify',
          src: require('@/assets/techicons/vuetifyjs.svg'),
          text: 'Vuetify is a Material Design component framework for Vue.js.',
          homepage: 'https://vuetifyjs.com/',
        },
        Typescript: {
          name: 'Typescript',
          src: require('@/assets/techicons/typescript-icon.svg'),
          text: 'TypeScript extends JavaScript by adding types.',
          homepage: 'https://www.typescriptlang.org/',
        },
        Javascript: {
          name: 'Javascript',
          src: require('@/assets/techicons/javascript.svg'),
          text:
            'JavaScript is a scripting or programming language that allows you to implement complex features on web pages',
          homepage:
            'https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/What_is_JavaScript',
        },
        HTML5: {
          name: 'HTML5',
          src: require('@/assets/techicons/html-5.svg'),
          text: 'HTML is the World Wide Web’s core markup language.',
          homepage:
            'https://www.w3.org/TR/html52/introduction.html#introduction',
        },
        CSS3: {
          name: 'CSS3',
          src: require('@/assets/techicons/css-3.svg'),
          text: 'Cascading Style Sheets',
          homepage: 'https://www.w3.org/TR/selectors-3/',
        },
        SASS: {
          name: 'SASS',
          src: require('@/assets/techicons/sass.svg'),
          text:
            'Sass is the most mature, stable, and powerful professional grade CSS extension language in the world.',
          homepage: 'https://sass-lang.com/',
        },
        Babel: {
          name: 'Babel',
          src: require('@/assets/techicons/babel.svg'),
          text: 'Babel is a JavaScript compiler.',
          homepage: 'https://babeljs.io/',
        },
        Yarn: {
          name: 'Yarn',
          src: require('@/assets/techicons/yarn.svg'),
          text:
            'Yarn is a package manager that doubles down as project manager. ',
          homepage: 'https://yarnpkg.com/',
        },
        ESlint: {
          name: 'ESlint',
          src: require('@/assets/techicons/eslint.svg'),
          text: 'Find and fix problems in your JavaScript code',
          homepage: 'https://eslint.org/',
        },
        Prettier: {
          name: 'Prettier',
          src: require('@/assets/techicons/prettier.svg'),
          text: 'An opinionated code formatter',
          homepage: 'https://prettier.io/',
        },
        Nodejs: {
          name: 'Nodejs',
          src: require('@/assets/techicons/nodejs.svg'),
          text:
            "Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine.",
          homepage: 'https://nodejs.org/en/',
        },
        Jest: {
          name: 'Jest',
          src: require('@/assets/techicons/jest.svg'),
          text:
            'Jest is a delightful JavaScript Testing Framework with a focus on simplicity.',
          homepage: 'https://jestjs.io/',
        },
        Contentful: {
          name: 'Contentful',
          src: require('@/assets/techicons/contentful.svg'),
          text: 'It’s the easiest, fastest way to manage content',
          homepage: 'https://www.contentful.com/',
        },
        Sentry: {
          name: 'Sentry',
          src: require('@/assets/techicons/sentry-icon.svg'),
          text:
            "Sentry's application monitoring platform helps every developer diagnose, fix, and optimize the performance of their code.",
          homepage: 'https://sentry.io/welcome/',
        },
        Netlify: {
          name: 'Netlify',
          src: require('@/assets/techicons/netlify.svg'),
          text:
            'An intuitive Git-based workflow and powerful serverless platform to build, deploy, and collaborate on web apps',
          homepage: 'https://www.netlify.com/',
        },
        Jamstack: {
          name: 'Jamstack',
          src: require('@/assets/techicons/jamstack-icon.svg'),
          text:
            'The modern way to build Websites and Apps that delivers better performance',
          homepage: 'https://jamstack.org/',
        },
      },
      selectItem: 'Nuxt',
    }
  },
  computed: {
    iconheight() {
      switch (this.$vuetify.breakpoint.name) {
        case 'xs':
          return 30
        case 'sm':
          return 30
        case 'md':
          return 50
        case 'lg':
          return 80
        case 'xl':
          return 50
        default:
          return 0
      }
    },
  },
})
</script>
<style lang="scss">
.tech-wrap {
  &__view {
    &--img-a {
      display: block;
      height: 100%;
    }
  }
}
</style>
