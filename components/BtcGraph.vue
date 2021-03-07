<template>
  <div class="btcgraph-wrap"><div id="chart-container"></div></div>
</template>
<script lang="ts">
import Vue from 'vue'
const CryptowatchEmbed = require('cryptowatch-embed')

export default Vue.extend({
  name: 'BtcGraph',
  mounted() {
    const chart = new CryptowatchEmbed('bitfinex', 'btcusd', {
      width: 800,
      height: 500,
    })
    chart.mount('#chart-container')
  },
})
</script>
