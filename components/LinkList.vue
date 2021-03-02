<template>
  <div class="linklist">
    <div class="linklist__header">
      <v-container class="linklist__header--container">
        <v-row class="linklist__header--row">
          <v-col cols="6"
            ><h2 class="linklist__header--title">リンク集</h2></v-col
          >
          <v-spacer></v-spacer>
          <v-col cols="5" class="linklist__header--select"
            ><v-select
              v-model="CategoryValue"
              :items="items"
              item-text="state"
              item-value="abbr"
              label="Category"
              multiple
              chips
            ></v-select
          ></v-col>
        </v-row>
      </v-container>
    </div>
    <ul class="linklist__list">
      <li v-for="obj in linklist" :key="obj.name" class="linklist__list--item">
        <v-card>
          {{ obj.name }}
        </v-card>
      </li>
    </ul>
    <div class="linklist__pagination">
      <v-pagination circle></v-pagination>
    </div>
  </div>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'LinkList',
  data() {
    return {
      linklist: [
        {
          name: 'いきいき音楽科',
          link: 'https://www.iki2music.work/',
          text: 'https://www.iki2music.work/',
          category: ['music', 'theory'],
        },
        {
          name: 'DATT.MUSIC',
          link: 'https://datt-music.com/',
          text: 'https://datt-music.com/',
          category: ['music'],
        },
        {
          name: '音楽理論.com',
          link: 'https://ongakuriron.com/',
          text: 'https://ongakuriron.com/',
          category: ['music', 'theory'],
        },
        {
          name: 'Arch Wiki',
          link: 'https://www.archlinux.jp/',
          text: 'https://www.archlinux.jp/',
          category: ['it'],
        },
        {
          name: 'Zenn',
          link: 'https://zenn.dev/',
          text: 'https://zenn.dev/',
          category: ['it'],
        },
        {
          name: 'Qiita',
          link: 'https://qiita.com/',
          text: 'https://qiita.com/',
          category: ['it'],
        },
        {
          name: 'ITmedia',
          link: 'http://www.itmedia.co.jp/',
          text: 'http://www.itmedia.co.jp/',
          category: ['it'],
        },
        {
          name: 'さくらのナレッジ',
          link: 'https://knowledge.sakura.ad.jp/',
          text: 'https://knowledge.sakura.ad.jp/',
          category: ['it'],
        },
        {
          name: 'ICSMedia',
          link: 'https://ics.media/',
          text: 'https://ics.media/',
          category: ['it'],
        },
        {
          name: 'Wolframalpha',
          link: 'https://www.wolframalpha.com/',
          text: 'https://www.wolframalpha.com/',
          category: ['math'],
        },
      ],
      items: [
        { state: 'Music', abbr: 'music' },
        { state: 'MusicTheory', abbr: 'theory' },
        { state: 'IT', abbr: 'it' },
        { state: 'Math', abbr: 'math' },
        { state: 'Audio', abbr: 'audio' },
      ],
      CategoryValue: [],
    }
  },
})
</script>
<style lang="scss" scoped>
.linklist {
  &__header {
    &--title {
      font-size: 27px;
      text-align: left;
      margin-top: 20px;
      margin-bottom: 0px;
    }
  }
  &__list {
    list-style: none;
  }
}
</style>
