<template>
  <div class="download-wrap"><Dlc /></div>
</template>
<script lang="ts">
import Vue from 'vue'
import Dlc from '@/components/Dlc.vue'
export default Vue.extend({
  components: {
    Dlc,
  },
  data() {
    return {
      title: 'Download',
    }
  },
  head() {
    return {
      title: 'Download',
      meta: [
        {
          hid: 'Download',
          name: 'Download',
          content: 'Download',
        },
      ],
    }
  },
})
</script>
