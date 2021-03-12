<template>
  <div class="spec-wrap"><Profile /></div>
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
      title: 'Spec',
    }
  },
  head() {
    return {
      title: 'Spec',
      meta: [
        {
          hid: 'Spec',
          name: 'Spec',
          content: 'Spec',
        },
      ],
    }
  },
})
</script>
