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
      <li v-for="obj in linklists" :key="obj.name" class="linklist__list--item">
        <v-hover v-slot="{ hover }">
          <v-card class="linklist__list--vcard" :elevation="hover ? 10 : 2">
            <a
              class="linklist__list--vcard--link"
              :href="obj.link"
              target="_blank"
              rel="noopener noreferrer"
              >{{ obj.name }}</a
            >
          </v-card>
        </v-hover>
      </li>
    </ul>
    <div class="linklist__pagination">
      <v-pagination
        v-model="currentPage"
        circle
        :length="pageLength > 0 ? pageLength : 1"
        :total-visible="5"
      ></v-pagination>
    </div>
  </div>
</template>
<script lang="ts">
import Vue from 'vue'

interface linkslistObject {
  name: string
  link: string
  text: string
  category: string[]
}
export default Vue.extend({
  name: 'LinkList',
  props: {
    linklists: {
      type: Array as Vue.PropType<linkslistObject[]>,
      default() {
        return [
          { text: 'none', link: 'none', name: 'none', category: ['music'] },
        ]
      },
    },
    totalLength: {
      type: Number,
      default: 1,
    },
  },
  data() {
    return {
      // linkslists: [
      //   {
      //     name: 'いきいき音楽科',
      //     link: 'https://www.iki2music.work/',
      //     text: 'https://www.iki2music.work/',
      //     category: ['music', 'theory'],
      //   },
      //   {
      //     name: 'DATT.MUSIC',
      //     link: 'https://datt-music.com/',
      //     text: 'https://datt-music.com/',
      //     category: ['music'],
      //   },
      //   {
      //     name: '音楽理論.com',
      //     link: 'https://ongakuriron.com/',
      //     text: 'https://ongakuriron.com/',
      //     category: ['music', 'theory'],
      //   },
      //   {
      //     name: 'Arch Wiki',
      //     link: 'https://www.archlinux.jp/',
      //     text: 'https://www.archlinux.jp/',
      //     category: ['it'],
      //   },
      //   {
      //     name: 'Zenn',
      //     link: 'https://zenn.dev/',
      //     text: 'https://zenn.dev/',
      //     category: ['it'],
      //   },
      //   {
      //     name: 'Qiita',
      //     link: 'https://qiita.com/',
      //     text: 'https://qiita.com/',
      //     category: ['it'],
      //   },
      //   {
      //     name: 'ITmedia',
      //     link: 'http://www.itmedia.co.jp/',
      //     text: 'http://www.itmedia.co.jp/',
      //     category: ['it'],
      //   },
      //   {
      //     name: 'さくらのナレッジ',
      //     link: 'https://knowledge.sakura.ad.jp/',
      //     text: 'https://knowledge.sakura.ad.jp/',
      //     category: ['it'],
      //   },
      //   {
      //     name: 'ICSMedia',
      //     link: 'https://ics.media/',
      //     text: 'https://ics.media/',
      //     category: ['it'],
      //   },
      //   {
      //     name: 'Wolframalpha',
      //     link: 'https://www.wolframalpha.com/',
      //     text: 'https://www.wolframalpha.com/',
      //     category: ['math'],
      //   },
      // ],
      items: [
        { state: 'Music', abbr: 'music' },
        { state: 'MusicTheory', abbr: 'theory' },
        { state: 'IT', abbr: 'it' },
        { state: 'Math', abbr: 'math' },
        { state: 'Audio', abbr: 'audio' },
      ],
      CategoryValue: [],
      currentPage: 1,
    }
  },
  computed: {
    pageLength() {
      return Math.ceil(this.totalLength / 5)
    },
  },
  watch: {
    currentPage(newNumber: string) {
      this.$router.push({ name: 'Links', query: { page: newNumber } })
    },
  },
  mounted() {
    const query = this.$route.query.page
    this.currentPage = query != null ? Number(query) : 1
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
    padding: 0 30px;
    list-style: none;
    // display: flex;
    // flex-wrap: wrap;
    // justify-content: space-around;
    &--vcard {
      font-size: 30px;
      height: 100px;
      // width: 400px;
      margin: 0 auto;
      margin-bottom: 20px;
      &--link {
        text-decoration: none;
        display: block;
        height: 100%;
        color: black;
      }
    }
  }
}
</style>
