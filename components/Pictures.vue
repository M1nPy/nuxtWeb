<template>
  <div class="pictures-wrap">
    <v-container>
      <v-row>
        <v-card class="flex">
          <v-card-title
            ><h3 class="history-wrap__header--title">Gallery</h3>
            <v-spacer></v-spacer>
            クリックで画像を拡大
          </v-card-title>
        </v-card>
      </v-row>
      <v-row>
        <v-col v-for="n in 9" :key="n" class="d-flex child-flex" cols="4">
          <v-dialog v-model="dialog" max-height="500px" max-width="800px">
            <template #activator="{ on, attrs }">
              <v-hover v-slot="{ hover }">
                <v-responsive
                  :class="{ 'on-hover': hover }"
                  :aspect-ratio="16 / 9"
                >
                  <v-img
                    :src="`https://picsum.photos/500/300?image=${n * 5 + 10}`"
                    :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
                    class="grey lighten-2"
                    v-bind="attrs"
                    @click="
                      imgUrl = `https://picsum.photos/500/300?image=${
                        n * 5 + 10
                      }`
                    "
                    v-on="on"
                  >
                    <template #placeholder>
                      <v-row
                        class="fill-height ma-0"
                        align="center"
                        justify="center"
                      >
                        <v-progress-circular
                          indeterminate
                          color="grey lighten-5"
                        ></v-progress-circular>
                      </v-row>
                    </template>
                  </v-img>
                </v-responsive>
              </v-hover>
            </template>
            <v-card>
              <v-img :src="imgUrl"></v-img>
            </v-card>
          </v-dialog>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'Pictures',
  data() {
    return {
      imgUrl: 'https://picsum.photos/500/300?image=1',
      dialog: false,
    }
  },
})
</script>
<style lang="scss" scoped>
.v-responsive:not(.on-hover) {
  opacity: 1;
}
.v-responsive {
  opacity: 0.5;
  transition: opacity 0.4s ease-in-out;
}
</style>
