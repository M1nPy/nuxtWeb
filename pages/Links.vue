<template>
  <div class="wrap__links">
    <v-app><LinkList /></v-app>
  </div>
</template>
<script lang="ts">
import LinkList from '@/components/LinkList.vue'
import Vue from 'vue'
export default Vue.extend({
  components: {
    LinkList,
  },
})
</script>
<style lang="sass" scoped></style>
