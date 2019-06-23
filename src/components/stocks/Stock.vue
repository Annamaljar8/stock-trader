<template>
  <div class="">
      <div class="card border-success mb-3">
        <div class="card-header">
            {{ stock.name }}
            <small>(Prise: {{ stock.price }})</small>
        </div>
        <div class="card-body text-success">
        <div class="form-row" style="text-align: end;">
            <div class="form-group col-md-8">
                <input
                    type="number"
                    class="form-control"
                    placeholder="Quantity"
                    v-model.number="quantity"
                    :class="{danger: insufficientFunds}"
                    >
            </div>
            <div class="form-group col-md-4 ">
                <button
                    class="btn btn-success"
                    @click="buyStock"
                    :disabled="insufficientFunds || quantity <= 0 || !Number.isInteger(quantity)"
                    >{{ insufficientFunds ? 'Insufficient Funds' : 'Buy' }}</button>
            </div>
        </div>
        </div>
    </div>
  </div>
</template>

<style scope>
    .danger {
        border: 1px solid red;
    }
</style>

<script>
    export default {
        props: ['stock'],
        data() {
            return {
                quantity: 0
            }
        },
        computed: {
            funds() {
                return this.$store.getters.funds;
            },
            insufficientFunds() {
                return this.quantity * this.stock.price > this.funds;
            }
        },
        methods: {
            buyStock() {
                const order = {
                    stockId: this.stock.id,
                    stockPrice: this.stock.price,
                    quantity: this.quantity
                }
                this.$store.dispatch('buyStock', order);
                this.quantity = 0;
                return false;

            },

        }
    }
</script>
