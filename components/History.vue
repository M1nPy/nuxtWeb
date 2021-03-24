<template>
  <div class="history-wrap">
    <v-container>
      <v-row>
        <v-col class="pa-0">
          <v-card class="flex">
            <v-card-title
              ><h3 class="history-wrap__header--title">History</h3>
              <v-spacer></v-spacer>
              <v-snackbar v-model="expand">
                <div style="text-align: center">
                  スクロールして表示してみましょう
                </div>
              </v-snackbar>
              <v-spacer></v-spacer>
              <v-btn @click="expand = !expand">
                <span v-show="!expand">ここをクリック</span>
                <span v-show="expand">もう一度クリック</span>
              </v-btn>
            </v-card-title>
          </v-card>
          <v-parallax
            height="300"
            :src="require('@/assets/header.JPG')"
          ></v-parallax>
        </v-col>
      </v-row>
      <v-row class="py-10">
        <v-spacer></v-spacer>
        <v-col cols="5">
          <transition-group
            class="history-wrap__list--left d-flex flex-column"
            tag="ul"
          >
            <li v-for="i in history1" :key="i.title">
              <v-lazy>
                <v-card class="history-wrap__list--left-items mx-auto">
                  <v-card-title>{{ i.title }}</v-card-title>
                  <v-card-text>{{ i.text }}</v-card-text></v-card
                >
              </v-lazy>
            </li>
          </transition-group>
        </v-col>
        <v-spacer></v-spacer>
        <v-col cols="5">
          <transition-group
            class="history-wrap__list--right d-flex flex-column"
            tag="ul"
          >
            <li v-for="i in history2" :key="i.title">
              <v-lazy>
                <v-card class="history-wrap__list--right-items mx-auto">
                  <v-card-title>{{ i.title }}</v-card-title>
                  <v-card-text>{{ i.text }}</v-card-text></v-card
                >
              </v-lazy>
            </li>
          </transition-group>
        </v-col>
        <v-spacer></v-spacer>
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
      // history2: [
      //   { title: '5年前期', text: 'なんかやった。' },
      //   { title: '4年前期', text: 'なんかやった。' },
      //   { title: '3年前期', text: 'なんかやった。' },
      //   { title: '2年前期', text: 'なんかやった。' },
      //   { title: '1年前期', text: 'なんかやった。' },
      // ],
      // history1: [
      //   { title: '5年後期', text: 'なんかやった。' },
      //   { title: '4年後期', text: 'なんかやった。' },
      //   { title: '3年後期', text: 'なんかやった。' },
      //   { title: '2年後期', text: 'なんかやった。' },
      //   { title: '1年後期', text: 'なんかやった。' },
      // ],
      history2: [
        { title: '未実装', text: '未実装' },
        { title: '未実装', text: '未実装' },
        { title: '未実装', text: '未実装' },
        { title: '未実装', text: '未実装' },
        { title: '未実装', text: '未実装' },
      ],
      history1: [
        { title: '未実装', text: '未実装' },
        { title: '未実装', text: '未実装' },
        { title: '未実装', text: '未実装' },
        { title: '未実装', text: '未実装' },
        { title: '未実装', text: '未実装' },
      ],
      expand: false,
    }
  },
  mounted() {},
  methods: {},
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
  }
  &__list--left {
    list-style: none;
    padding: 0;
  }
}
</style>
