<template>
  <div class="orders">
    <div v-for="order in orders" :key="order.id">
      <Order v-if="order" :order="order" @confirmOrder="confirmOrder" @denyOrder="denyOrder"/>
    </div>
  </div>
</template>

<script>
import Order from './Order.vue'

export default {
  name: 'Orders',
  methods: {
    confirmOrder(order) {
        this.$emit("confirmOrder", order)
    },
    denyOrder(order) {
        this.$emit("denyOrder", order)
    }
  },
  props: {
    orders: Array
  },
  components: {
    Order
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
