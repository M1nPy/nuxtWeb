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
              v-model="categoryValue"
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
    <div class="linklist__list">
      <transition-group
        tag="ul"
        name="flip-list"
        class="linklist__list--transition"
      >
        <li
          v-for="obj in linklists"
          :key="obj.name"
          class="linklist__list--item"
        >
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
      </transition-group>
    </div>
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
interface selectList {
  state: string
  abbr: string
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
    items: {
      type: Array as Vue.PropType<selectList[]>,
      default: [
        { state: 'Music', abbr: 'music' },
        { state: 'IT', abbr: 'it' },
      ],
    },
  },
  data() {
    return {
      categoryValue: [''],
      currentPage: 1,
    }
  },
  computed: {
    pageLength() {
      return Math.ceil(this.totalLength / 3)
    },
  },
  watch: {
    currentPage(newNumber: string) {
      this.$router.push({
        name: 'Links',
        query: {
          category: this.categoryValue.filter(Boolean).join(),
          page: newNumber,
        },
      })
    },
    categoryValue(newCategory) {
      this.$router.push({
        query: { category: newCategory.filter(Boolean).join(), page: '1' },
      })
      this.currentPage = 1
    },
  },
  mounted() {
    const query = this.$route.query.page
    this.currentPage = query != null ? Number(query) : 1

    const categoryq = this.$route.query.category
    this.categoryValue = categoryq != null ? String(categoryq).split(',') : []
  },
})
</script>
<style lang="scss" scoped>
.flip-list {
  &-enter {
    opacity: 0;
    transform: translateX(30px);
  }
  &-leave-active {
    position: absolute;
  }
  &-enter-active {
    transition: all 0.5s ease;
  }
  &-leave-to {
    opacity: 0;
    transform: translateX(30px);
  }
}
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
    &--transition {
      padding: 0 30px;
      list-style: none;
      height: 500px; //button Fixed
    }
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
