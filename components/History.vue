<template>
  <div class="history-wrap">
    <v-container>
      <v-row>
        <v-col cols="5">
          <transition-group
            class="history-wrap__list--left d-flex flex-column"
            tag="ul"
          >
            <li v-for="i in history" :key="i.text">
              <v-card
                class="history-wrap__list--left-items mx-auto"
                height="200"
                width="500"
                >{{ i.text }}</v-card
              >
            </li>
          </transition-group>
        </v-col>
        <v-divider></v-divider>
        <v-col cols="5">
          <transition-group
            class="history-wrap__list--right d-flex flex-column"
            tag="ul"
          >
            <li v-for="i in history" :key="i.text">
              <v-card
                class="history-wrap__list--right-items mx-auto"
                height="200"
                width="500"
                >{{ i.text }}</v-card
              >
            </li>
          </transition-group>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'History',
  data() {
    return {
      history: [
        { text: 'あいうえお' },
        { text: 'いうえおか' },
        { text: 'うえおかき' },
        { text: 'えおかきく' },
      ],
    }
  },
})
</script>
<style lang="scss" scoped>
.history-wrap {
  &__list--right {
    list-style: none;
    padding: 0;
    &-items {
      margin-top: 200px;
    }
  }
  &__list--left {
    list-style: none;
    padding: 0;

    &-items {
      margin-bottom: 200px;
    }
  }
}
</style>
