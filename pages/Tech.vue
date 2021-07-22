<template>
  <div class="Tech-wrap"><Tech /></div>
</template>
<script lang="ts">
import Vue from 'vue'
import Tech from '@/components/Tech.vue'
export default Vue.extend({
  components: {
    Tech,
  },
  data() {
    return {
      title: 'Tech',
    }
  },
  head() {
    return {
      title: 'Tech',
      meta: [
        {
          hid: 'Tech',
          name: 'Tech',
          content: 'Tech',
        },
      ],
    }
  },
})
</script>
