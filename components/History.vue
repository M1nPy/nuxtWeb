<template>
  <div class="history-wrap">
    <v-container>
      <v-row>
        <v-card class="flex">
          <v-card-title
            ><h3 class="history-wrap__header--title">History</h3>
            <v-spacer></v-spacer>
            <v-snackbar v-model="expand">
              <div style="text-align: center">スクロールすると表示されます</div>
            </v-snackbar>
            <v-spacer></v-spacer>
            <v-btn @click="expand = !expand">
              <span v-show="!expand">ここをクリック</span>
              <span v-show="expand">もう一度クリック</span>
            </v-btn>
          </v-card-title>
          <v-img
            height="300"
            src="https://cdn.pixabay.com/photo/2021/02/07/09/11/sunset-5990540_640.jpg"
          ></v-img>
        </v-card>
      </v-row>
      <v-row class="py-10">
        <v-col cols="5">
          <transition-group
            class="history-wrap__list--left d-flex flex-column"
            tag="ul"
          >
            <li v-for="(i, index) in history1" :key="i.title">
              <v-card
                :id="'itemanime' + 2 * index"
                class="history-wrap__list--left-items mx-auto"
              >
                <v-responsive :aspect-ratio="16 / 9">
                  <v-card-title>{{ i.title }}</v-card-title>
                  <v-card-text>{{ i.text }}</v-card-text></v-responsive
                ></v-card
              >
            </li>
          </transition-group>
        </v-col>
        <v-spacer></v-spacer>
        <v-col cols="5">
          <transition-group
            class="history-wrap__list--right d-flex flex-column"
            tag="ul"
          >
            <li v-for="(i, index) in history2" :key="i.title">
              <v-card
                :id="'itemanime' + (2 * index + 1)"
                class="history-wrap__list--right-items mx-auto"
                ><v-responsive :aspect-ratio="16 / 9">
                  <v-card-title>{{ i.title }}</v-card-title>
                  <v-card-text>{{ i.text }}</v-card-text>
                </v-responsive></v-card
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
      history2: [
        { title: '5年前期', text: 'なんもしてない。' },
        { title: '4年前期', text: 'なんもしてない。' },
        { title: '3年前期', text: 'なんもしてない。' },
        { title: '2年前期', text: 'なんもしてない。' },
        { title: '1年前期', text: 'なんもしてない。' },
      ],
      history1: [
        { title: '5年後期', text: 'なんもしてない。' },
        { title: '4年後期', text: 'なんもしてない。' },
        { title: '3年後期', text: 'なんもしてない。' },
        { title: '2年後期', text: 'なんもしてない。' },
        { title: '1年後期', text: 'なんもしてない。' },
      ],
      expand: false,
    }
  },
  mounted() {
    for (let i = -1; i < 9; i++) {
      this.$scrollmagic.addScene(this.getscene(i))
    }
  },
  methods: {
    getscene(index) {
      return this.$scrollmagic
        .scene({
          triggerElement: '#itemanime' + String(index < 0 ? 0 : index),
          triggerHook: 0.3,
          offset: -200 - 130 * (index < 0 ? 0.05 : index),
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
  &__header {
    &--title {
      text-align: center;
    }
    &--ctext {
      text-align: center;
    }
  }
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
      transition: 1s all cubic-bezier(0.39, 0.575, 0.565, 1);
    }
  }
}
</style>
