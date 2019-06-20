<template>
  <div class="">
      <div class="card border-primary mb-3">
        <div class="card-header">
            {{ stock.name }}
            <small>(Prise: {{ stock.price }} | Quantity: {{ stock.quantity }})</small>
        </div>
        <div class="card-body text-primary">
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
                    class="btn btn-primary"
                    @click="sellStock"
                    :disabled="quantity <= 0 || !Number.isInteger(quantity)"
                    >Sell</button>
            </div>
        </div>
        </div>
    </div>
  </div>
</template>

<script>
import {mapActions} from 'vuex';
    export default {
        props: ['stock'],
        data() {
            return {
                quantity: 0
            }
        },
        methods: {
            ...mapActions({
                placeSellOrder: 'sellStock'
            }),
            sellStock() {
                const order = {
                    stockId: this.stock.id,
                    stockPrice: this.stock.price,
                    quantity: this.quantity
                };
                this.placeSellOrder(order);
            }
        },
    }
</script>
