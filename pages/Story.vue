<template>
  <div class="story-wrap"><BtcGraph /></div>
</template>
<script lang="ts">
import Vue from 'vue'
import BtcGraph from '@/components/BtcGraph.vue'
export default Vue.extend({
  components: {
    BtcGraph,
  },
})
</script>
