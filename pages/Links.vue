<template>
  <div class="wrap__links">
    <v-container>
      <v-row>
        <v-col cols="0" lg="2"></v-col>
        <v-col cols="12" lg="8">
          <LinkList />
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
  asyncData() {
    return client.getEntries().then((entries) => {
      return { post: entries.items }
    })
  },
})
</script>
<style lang="sass" scoped></style>
