<template>
  <div class="order">
      <!-- {{order}}
      <button @click="confirmOrder">Confirm</button>
      <button @click="denyOrder">Deny</button> -->
      <div style="border: 1px solid green ; width: 200px; margin: 12px; padding: 20px 0;">
        <h4>Name: {{order.user}}</h4>
        <h4>Status: {{order.confirmed}}</h4>
        <table style="width:100%">
          <tr>
            <th>Item</th>
            <th>Count</th>
          </tr>
          <tr v-for="(order, i) in order.cart" :key="i">
            <td>{{order.name}}</td>
            <td>{{order.count}}</td>
          </tr>
        </table>
        <button @click="confirmOrder">Confirm</button>
        <button @click="denyOrder">Deny</button>
      </div>
  </div>
</template>

<script>
export default {
  name: 'Order',
  methods: {
    confirmOrder() {
        this.$emit("confirmOrder", this.order)
    },
    denyOrder() {
        this.$emit("denyOrder", this.order)
    }
  },
  props: {
    order: Object
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
