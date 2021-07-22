<template>
  <div class="profile-wrap">
    <v-container>
      <v-row>
        <v-spacer></v-spacer>
        <v-col cols="11" lg="8">
          <v-card class="my-10" width="100%">
            <v-container>
              <v-row>
                <v-col class="pt-6" align="center">
                  <v-card-title
                    class="justify-center mx-auto my-10 text-h3 text-sm-h1"
                  >
                    M1nPy
                  </v-card-title>
                </v-col>
              </v-row>
              <v-row>
                <v-col class="mb-8" align="center">
                  <v-avatar size="150" class="justify-center">
                    <v-img
                      :src="require('@/assets/logo.png')"
                      class="my-3"
                      contain
                    />
                  </v-avatar>
                </v-col>
              </v-row>
              <v-row>
                <v-col class="mb-8 text-center">
                  <p class="subtitle-1">
                    趣味はプログラミング、ピアノ、音楽理論、登山、キャンプ、自作PC、気象学、アニメ、ADVです。<br />
                    JazzやJFN系列のラジオを好んで聞きます。<br />
                    専攻は電気情報工学です。<br />
                    最近は主にPythonとNuxtを使っています。
                  </p>
                </v-col>
              </v-row>

              <v-row>
                <v-col class="pt-6">
                  <v-card-title class="text-h4 text-sm-h3"
                    ><div class="mx-auto my-8 justify-center">
                      Contents
                    </div></v-card-title
                  >
                </v-col>
              </v-row>
              <v-row v-for="items in profile" :key="items.title" class="my-16">
                <v-col flex cols="6" class="text-h5 text-sm-h4 contents-title">
                  {{ items.title }}
                </v-col>
                <v-col cols="6 align-self-center">
                  <v-row>
                    <v-col>
                      <v-icon>mdi-account-box</v-icon>
                      <span>{{ items.name }}</span>
                    </v-col></v-row
                  >
                  <v-row
                    ><v-col class="overline">
                      <v-icon>mdi-link-variant</v-icon
                      ><a
                        :href="items.url"
                        target="_blank"
                        rel="noopener noreferrer"
                        >{{ items.url.slice(0, 25) }}...</a
                      >
                    </v-col></v-row
                  >
                </v-col>
              </v-row>
              <!-- contact -->
              <v-row>
                <v-col class="pt-6" align="center">
                  <v-card-title class="text-h4 text-sm-h3 justify-center"
                    ><div class="my-8">Contact</div></v-card-title
                  >
                </v-col>
              </v-row>
              <v-row class="mb-12 mt-6">
                <v-col
                  v-for="items in contact"
                  :key="items.means"
                  class="text-center"
                >
                  <a :href="items.url" style="text-decoration: none">
                    <v-icon size="64"> {{ items.icon }} </v-icon></a
                  >
                </v-col>
              </v-row>
            </v-container>
          </v-card>
        </v-col>
        <v-spacer></v-spacer>
      </v-row>
    </v-container>
  </div>
</template>
<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'Profile',
  data() {
    return {
      contact: [
        { icon: 'mdi-discord', means: 'Discord', url: 'M1nPy#8777' },
        {
          icon: 'mdi-twitter',
          means: 'Twitter',
          url: 'https://twitter.com/m1npy',
        },
        {
          icon: 'mdi-github',
          means: 'Github',
          url: 'https://github.com/M1nPy',
        },
        { icon: 'mdi-link-variant', means: 'Website', url: 'm1npy.com' },
      ],
      profile: [
        {
          title: 'Osu!',
          name: 'M1nPy',
          url: 'https://osu.ppy.sh/users/10363375',
        },
        {
          title: 'ErogameSpace',
          name: 'M1nPy',
          url:
            'https://erogamescape.dyndns.org/~ap2/ero/toukei_kaiseki/user_infomation.php?user=M1nPy',
        },
        {
          title: 'YAMAP',
          name: 'M1nPy',
          url: 'https://yamap.com/users/1687023',
        },
        {
          title: 'Youtube',
          name: 'modernparachute',
          url: 'https://www.youtube.com/channel/UCMAmj-08fJFbyhPRcivqGhg',
        },
      ],
    }
  },
})
</script>
<style lang="scss" scoped>
.profile {
  &-wrap {
    background: url(~@/assets/status_background.jpg);
  }
}
.contents {
  &-title {
    // white-space: pre-line;
    word-wrap: break-word;
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
</style>
