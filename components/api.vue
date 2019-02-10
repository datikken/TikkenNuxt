<template>
  <div>
    <h1>Парсим bitcoin</h1>
    <div v-for="currency in info" :key="currency.id" class="currency">
      {{ currency.description }}
      <span class="lighten">
        <span class="numbers" v-html="currency.symbol" />{{ currency.rate_float }}
      </span>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      info: null
    }
  },
  mounted() {
    axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => (this.info = response.data.bpi))
  }
}
</script>

<style scoped>
.numbers {
  margin: 0 20px 0 20px;
}
</style>
