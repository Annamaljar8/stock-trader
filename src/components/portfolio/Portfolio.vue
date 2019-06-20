<template>
  <div class="row p-3" style="justify-content: space-between;">
      <app-stock v-for="stock in stocks" :key="stocks.id" :stock="stock"></app-stock>
  </div>
</template>

<script>
    import {mapGetters} from 'vuex';
    import Stock from './Stock.vue';

    export default {
        computed: {
            ...mapGetters({
                stocks: 'stockPortfolio'
            })
        },
        components: {
            appStock: Stock
        },
    }
</script>
