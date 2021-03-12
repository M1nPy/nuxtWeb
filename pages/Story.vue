<template>
  <div class="story-wrap"><History /></div>
</template>
<script lang="ts">
import Vue from 'vue'
import History from '@/components/History.vue'
export default Vue.extend({
  components: {
    History,
  },
  data() {
    return {
      title: 'Story',
    }
  },
  head() {
    return {
      title: 'Story',
      meta: [
        {
          hid: 'Story',
          name: 'Story',
          content: 'Story',
        },
      ],
    }
  },
})
</script>
