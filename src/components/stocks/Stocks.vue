<template>
  <div class="row">
      <app-stock v-for="stock in stocks"></app-stock>
  </div>
</template>

<script>
import Stock from './Stock.vue';
    export default {
        data() {
            return {
                stocks: [
                    { id: 1, name: 'BMW', prise: 110 },
                    { id: 2, name: 'Google', prise: 200 },
                    { id: 3, name: 'Apple', prise: 250 },
                    { id: 4, name: 'Twitter', prise: 8 },
                ]
            }
        },
        components: {
            appStock: Stock
        }
    }
</script>
