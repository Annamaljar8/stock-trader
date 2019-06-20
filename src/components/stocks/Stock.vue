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
                    v-model.number="quantity">
            </div>
            <div class="form-group col-md-4 ">
                <button
                    class="btn btn-success"
                    @click="buyStock"
                    :disabled="quantity <= 0 || !Number.isInteger(quantity)"
                    >Buy</button>
            </div>
        </div>
        </div>
    </div>
  </div>
</template>

<script>
    export default {
        props: ['stock'],
        data() {
            return {
                quantity: 0
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
