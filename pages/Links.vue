<template>
  <div class="wrap__links">
    <v-container>
      <v-row>
        <v-col cols="0" lg="2"></v-col>
        <v-col cols="12" lg="8">
          <LinkList
            :linklists="
              post.items.map(function (x) {
                return x.fields
              })
            "
            :items="
              Spost.items.map(function (x) {
                return x.fields
              })
            "
            :total-length="post.total"
          />
        </v-col>
        <v-col cols="0" lg="2"></v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script lang="ts">
import LinkList from '@/components/LinkList.vue'
import Vue from 'vue'
import { createClient } from '~/plugins/contentful.js'

const client = createClient()

export default Vue.extend({
  components: {
    LinkList,
  },
  async asyncData({ query }) {
    const entries = await client.getEntries({
      content_type: 'linksLists',
      limit: 3,
      order: '-sys.type',
      skip: query.page ? (Number(query.page) - 1) * 3 : 0,
      'fields.category[all]': query.category ? query.category : 'music',
      // 'fields.tags.sys.contentType.sys.id': 'tags',
      // 'fields.tags.fields.tags': '',
    })
    const Sentries = await client.getEntries({
      content_type: 'linksListsSelects',
      order: '-sys.type',
    })
    return {
      post: entries,
      Spost: Sentries,
    }
  },
  watchQuery: true,
  // mounted():{

  // }
})
</script>
<style lang="sass" scoped></style>
