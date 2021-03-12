<template>
  <div class="gallery-wrap"><Pictures /></div>
</template>
<script lang="ts">
import Vue from 'vue'
import Pictures from '@/components/Pictures.vue'
export default Vue.extend({
  components: {
    Pictures,
  },
  data() {
    return {
      title: 'Gallery',
    }
  },
  head() {
    return {
      title: 'Gallery',
      meta: [
        {
          hid: 'Gallery',
          name: 'Gallery',
          content: 'Gallery',
        },
      ],
    }
  },
})
</script>
