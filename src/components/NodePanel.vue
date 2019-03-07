<template>
  <div class="panel">
    <Orders :orders="orders" @confirmOrder="confirmOrder" @denyOrder="denyOrder"/>
  </div>
</template>

<script>
import Orders from './Orders.vue'

export default {
  name: 'NodePanel',
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
    Orders
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
