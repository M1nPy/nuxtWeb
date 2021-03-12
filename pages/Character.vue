<template>
  <div class="character-wrap"><Tech /></div>
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
      title: 'Character',
    }
  },
  head() {
    return {
      title: 'Character',
      meta: [
        {
          hid: 'Character',
          name: 'Character',
          content: 'Character',
        },
      ],
    }
  },
})
</script>
