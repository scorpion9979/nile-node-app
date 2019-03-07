<template>
  <div class="debug">
      <button @click="addorder">Add Order</button>
      <button @click="debug">Dubug</button>
      <br/>
      <br/>
      <input v-model="user"  placeholder="Name of buyer (user)"/>
      <br/>
      <div v-for="(order, i) in cart" :key="i">
        <input v-if="order" v-model="order.name" placeholder="Name of item to be bought">
        <br/>
        <input v-if="order" v-model="order.count" placeholder="Item Count">
      </div>
  </div>
</template>

<script>

export default {
  name: 'ApiSimulation',
  methods: {
    debug() {
        this.$emit("debug", JSON.parse(JSON.stringify({
            user: this.user,
            cart: this.cart,
            confirmed: this.confirmed
      })))
    },
    addorder() {
      this.cart.push({ id: this.cart.length + 1, name: "", count: 1});
    }
  },
  data: function() {
      return {
          user: "",
          cart: [{ id: 1, name: '', count: 1},],
          confirmed: false
      }
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
