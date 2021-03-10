<template>
  <div class="profile-wrap">
    <v-container>
      <v-row>
        <v-card class="flex">
          <v-card-title
            ><h3 class="history-wrap__header--title">Status</h3>
            <v-spacer></v-spacer>
          </v-card-title>
        </v-card>
      </v-row>
      <v-row>
        <v-img
          width="100%"
          max-height="1400px"
          :src="require('@/assets/max-bender-8kobOraz4O4-unsplash.jpg')"
        >
          <v-container>
            <v-row>
              <v-spacer></v-spacer>
              <v-col cols="11" lg="8">
                <v-card class="my-10" width="100%">
                  <v-container>
                    <v-row>
                      <v-spacer></v-spacer>
                      <v-col class="pt-6" cols="6">
                        <v-card-title class="text-h5 text-sm-h2"
                          ><div class="mx-auto">M1nPy</div></v-card-title
                        >
                      </v-col>
                      <v-spacer></v-spacer>
                    </v-row>
                    <v-row>
                      <v-spacer></v-spacer>
                      <v-col align-self="center" cols="8">
                        <v-card-text>
                          <p>
                            <v-icon>mdi-account-box</v-icon>
                            <span>M1nPy</span>
                          </p>
                          <p>
                            <v-icon>mdi-email</v-icon>
                            <span>Gmail:kagawakosen@...</span>
                          </p>
                          <p>
                            <v-icon>mdi-twitter</v-icon>
                            <a href="https://twitter.com/m1npy">@M1nPy</a>
                          </p>
                          <p>
                            <v-icon>mdi-link-variant</v-icon
                            ><a href="m1npy.com">m1npy.com</a>
                          </p>
                        </v-card-text>
                        <v-divider></v-divider>
                      </v-col>
                      <v-spacer></v-spacer>
                    </v-row>
                    <v-row>
                      <v-col cols="5">
                        <v-card-title class="text-h5 text-sm-h2"
                          ><div class="mx-auto">Osu!</div></v-card-title
                        >
                      </v-col>
                      <v-col cols="7">
                        <v-card-text>
                          <p>
                            <v-icon>mdi-account-box</v-icon>
                            <span>M1nPy</span>
                          </p>
                          <p>
                            <v-icon>mdi-crown</v-icon>
                            <span>#117,913 (noAPI)</span>
                          </p>
                          <p>
                            <v-icon>mdi-database</v-icon>
                            <!-- noAPI -->
                            <span>3413pp</span>
                          </p>
                          <p>
                            <v-icon>mdi-link-variant</v-icon
                            ><a href="https://osu.ppy.sh/users/10363375"
                              >https://osu.ppy.sh/users/10363375</a
                            >
                          </p>
                        </v-card-text>
                        <v-divider></v-divider>
                      </v-col>
                    </v-row>
                    <v-row>
                      <v-col cols="5">
                        <v-card-title class="text-h5 text-sm-h2"
                          ><div class="mx-auto" style="text-align: center">
                            Erogame<br />Scape
                          </div></v-card-title
                        >
                      </v-col>
                      <v-col cols="7">
                        <v-card-text>
                          <p>
                            <v-icon>mdi-account-box</v-icon>
                            <span>M1nPy</span>
                          </p>
                          <p>
                            <v-icon>mdi-shopping</v-icon>
                            <span>56</span>
                          </p>
                          <p>
                            <v-icon>mdi-check</v-icon>
                            <!-- noAPI -->
                            <span>19</span>
                          </p>
                          <p>
                            <v-icon>mdi-link-variant</v-icon
                            ><a
                              href="https://erogamescape.dyndns.org/~ap2/ero/toukei_kaiseki/user_infomation.php?user=M1nPy"
                              >https://erogamescape.dyndns.org</a
                            >
                          </p>
                        </v-card-text>
                        <v-divider></v-divider>
                      </v-col>
                    </v-row>
                    <v-row>
                      <v-col cols="5">
                        <v-card-title class="text-h5 text-sm-h2"
                          ><div class="mx-auto">YAMAP</div></v-card-title
                        >
                      </v-col>
                      <v-col cols="7">
                        <v-card-text>
                          <p>
                            <v-icon>mdi-account-box</v-icon>
                            M1nPy
                          </p>
                          <p>
                            <v-icon>mdi-medal</v-icon>
                            <!-- noAPI -->
                            Bronze
                          </p>
                          <p>
                            <v-icon>mdi-link-variant</v-icon
                            ><a href="https://yamap.com/users/1687023"
                              >https://yamap.com/users/1687023</a
                            >
                          </p>
                        </v-card-text>
                        <v-divider></v-divider>
                      </v-col>
                    </v-row>
                    <v-row>
                      <v-col cols="5">
                        <v-card-title class="text-h5 text-sm-h2"
                          ><div class="mx-auto">Youtube</div></v-card-title
                        >
                      </v-col>
                      <v-col cols="7">
                        <v-card-text>
                          <p>
                            <v-icon>mdi-account-box</v-icon>
                            <span>modern parachute</span>
                          </p>
                          <p>
                            <v-icon>mdi-link-variant</v-icon
                            ><a
                              href="https://www.youtube.com/channel/UCMAmj-08fJFbyhPRcivqGhg"
                              >modernparachute</a
                            >
                          </p>
                        </v-card-text>
                      </v-col>
                    </v-row>
                  </v-container>
                </v-card>
              </v-col>
              <v-spacer></v-spacer>
            </v-row>
          </v-container>
        </v-img>
      </v-row>
    </v-container>
  </div>
</template>
<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'Profile',
  data() {
    return {}
  },
})
</script>
