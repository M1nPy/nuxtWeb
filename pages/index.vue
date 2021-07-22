<template>
  <div class="index-wrap"><Profile /></div>
</template>
<script lang="ts">
import Vue from 'vue'
import Profile from '@/components/Profile.vue'
export default Vue.extend({
  components: {
    Profile,
  },
  data() {
    return {
      title: 'index',
    }
  },
  head() {
    return {
      title: 'index',
      meta: [
        {
          hid: 'index',
          name: 'index',
          content: 'index',
        },
      ],
    }
  },
})
</script>
