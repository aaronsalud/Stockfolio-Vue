<template>
    <v-flex>
        <v-card class="card">
            <div class="header">
                {{ stock.name}} (Price: {{stock.price}} | {{stock.quantity}})
            </div>
            <v-flex ma-3>
                <v-text-field label="Quantity" type="number" v-model="quantity"></v-text-field>
            </v-flex>
            <v-btn color="primary" @click="sell" :disabled="quantity <=0">Sell</v-btn>
        </v-card>
    </v-flex>
</template>


<script>
import { mapActions } from 'vuex'
export default {
  props: ['stock'],
  data: () => ({ quantity: 0 }),
  methods: {
    ...mapActions(['sellStock']),
    sell() {
      const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity
      }
      this.sellStock(order)
      this.quantity = 0
    }
  }
}
</script>
