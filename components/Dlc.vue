<template>
  <div class="dlc-wrap">
    <v-container>
      <v-row>
        <v-col
          ><v-card
            ><v-card-title><strong>あいうえお</strong></v-card-title>
            <v-card-text class="text-center">あいえお</v-card-text>
            <v-card-actions
              ><v-spacer></v-spacer><v-btn elevation="3">Download</v-btn>
              <v-spacer></v-spacer
            ></v-card-actions> </v-card
        ></v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'Dlc',
  data() {
    return {
      sel: [Number],
      items: [
        {
          id: 1,
          name: 'MusicSheets',
          children: [
            { id: 2, name: 'Calendar : app' },
            { id: 3, name: 'Chrome : app' },
            { id: 4, name: 'Webstorm : app' },
          ],
        },
        {
          id: 5,
          name: 'images',
          children: [
            { id: 6, name: 'Calendar : app' },
            { id: 7, name: 'Chrome : app' },
            { id: 8, name: 'Webstorm : app' },
          ],
        },
        {
          id: 9,
          name: 'other',
          children: [
            { id: 10, name: 'Calendar : app' },
            { id: 11, name: 'Chrome : app' },
            { id: 12, name: 'Webstorm : app' },
          ],
        },
      ],
    }
  },
})
</script>
