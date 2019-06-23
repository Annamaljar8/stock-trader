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
                    v-model.number="quantity"
                    :class="{danger: insufficientQuantity}"
                    >
            </div>
            <div class="form-group col-md-4 ">
                <button
                    class="btn btn-primary"
                    @click="sellStock"
                    :disabled="insufficientQuantity || quantity <= 0 || !Number.isInteger(quantity)"
                    >{{insufficientQuantity ? 'Not sell': 'Sell'}}</button>
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
import {mapActions} from 'vuex';
    export default {
        props: ['stock'],
        data() {
            return {
                quantity: 0
            }
        },
        computed:{
            insufficientQuantity() {
                return this.quantity > this.stock.quantity;
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
