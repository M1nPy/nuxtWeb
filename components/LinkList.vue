<template>
  <div class="linklist">
    <div class="linklist__header">
      <v-container class="linklist__header--container">
        <v-row class="linklist__header--row">
          <v-col cols="4"
            ><h2 style="text-align: center" class="linklist__header--title">
              リンク集
            </h2>
          </v-col>
          <v-col align-self="end" cols="4">
            <v-slider
              v-model="showNum"
              :thumb-color="'red'"
              :thumb-label="true"
              step="2"
              :label="String(showNum)"
              min="3"
              max="32"
            >
            </v-slider>
          </v-col>
          <v-col cols="4" class="linklist__header--select"
            ><v-select
              v-model="categoryValue"
              :items="items"
              item-text="state"
              item-value="abbr"
              label="Category"
              multiple
              chips
            >
              <template #selection="{ item, index }">
                <v-chip v-if="index === 0">
                  <span>{{ item.state }}</span>
                </v-chip>
                <span v-if="index === 1" class="grey--text caption">
                  (+{{ categoryValue.length - 1 }} others)
                </span>
              </template>
            </v-select></v-col
          >
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
          v-for="obj in SlicedLinks"
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
              >
                <v-container>
                  <v-row>
                    <v-card-title h1
                      ><strong class="text-lg-h4 text-h5 text-blue">{{
                        obj.name
                      }}</strong></v-card-title
                    ></v-row
                  >
                  <v-row class="mt-0"
                    ><v-col cols="7" lg="8" class="py-0">
                      <v-card-text v-if="screenSize() !== 'xs'">{{
                        obj.link.substr(0, 35) +
                        (obj.link.length > 35 ? '...' : ' ')
                      }}</v-card-text>
                    </v-col>
                    <v-col cols="5" lg="4" class="py-0" align-self="end"
                      ><v-card-text class="text-right">{{
                        obj.text
                      }}</v-card-text></v-col
                    >
                  </v-row></v-container
                >
              </a>
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
      categoryValue: [],
      currentPage: 1,
      showNum: 3,
    }
  },

  computed: {
    selected_linkslist() {
      const CategoryValue = (this as any).categoryValue
      return this.linklists.filter(function (linklist) {
        return (
          CategoryValue.map((item: string) =>
            linklist.category.includes(item)
          ).filter((x: Boolean) => x === true).length >= CategoryValue.length
        )
      })
    },
    pageLength(): number {
      this.updateCurrentPage(1)
      return Math.ceil(this.selected_linkslist.length / this.showNum)
    },
    SlicedLinks(): linkslistObject[] {
      const sn: number = this.showNum
      return this.selected_linkslist.slice(
        (this.currentPage - 1) * sn,
        (this.currentPage - 1) * sn + sn
      )
    },
  },
  methods: {
    updateCurrentPage(nextPage: number) {
      this.currentPage = nextPage
    },
    screenSize(): string {
      return (this as any).$vuetify.breakpoint.name
    },
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
    }
    &--vcard {
      font-size: 30px;
      // height: 90px;
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
