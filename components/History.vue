<template>
  <div class="history-wrap">
    <v-container>
      <v-row>
        <v-col cols="5">
          <transition-group
            class="history-wrap__list--left d-flex flex-column"
            tag="ul"
          >
            <li v-for="(i, index) in history" :key="i.text">
              <v-card
                :id="'itemanime' + 2 * index"
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
            <li v-for="(i, index) in history" :key="i.text">
              <v-card
                :id="'itemanime' + (2 * index + 1)"
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
<script>
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
  mounted() {
    for (let i = -1; i < 8; i++) {
      this.$scrollmagic.addScene(this.getscene(i))
    }
  },
  methods: {
    getscene(index) {
      return this.$scrollmagic
        .scene({
          triggerElement: '#itemanime' + String(index < 0 ? 0 : index),
          triggerHook: 0.3,
          offset: 220 - 130 * (index < 0 ? 0.05 : index),
          duration: 0,
          reverse: false,
        })
        .setTween('#itemanime' + String(index + 1), {
          css: {
            opacity: '1',
            transform: 'translate3d(0, 0, 0)',
          },
        })
        .addIndicators({ name: 'OK' })
    },
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
      transform: translate3d(500px, 0, 0);
      opacity: 0;
      transition: 1s all cubic-bezier(0.39, 0.575, 0.565, 1);
    }
  }
  &__list--left {
    list-style: none;
    padding: 0;

    &-items {
      margin-bottom: 200px;
      transform: translate3d(-500px, 0, 0);
      opacity: 0;
      transition: 0.5s all cubic-bezier(0.39, 0.575, 0.565, 1);
    }
  }
}
</style>
