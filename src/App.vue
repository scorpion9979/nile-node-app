<template>
  <div id="app">
    <NodePanel :orders="orders" @confirmOrder="confirmOrder" @denyOrder="denyOrder"/>
    <br/>
    <br/>
    <ApiSimulation @debug="debug"/>
  </div>
</template>

<script>
import NodePanel from './components/NodePanel.vue'
import ApiSimulation from './components/ApiSimulation.vue'

export default {
  name: 'app',
  methods: {
    confirmOrder(order) {
      this.orders.filter(o => o.id == order.id)[0].confirmed = true
    },
    denyOrder(order) {
      this.orders.filter(o => o.id == order.id)[0].confirmed = false
      this.orders = this.orders.filter(o => o.id != order.id)
    },
    debug({user, cart, confirmed}) {
      this.orders.push(({
        id: this.orders[this.orders.length - 1].id + 1,
        user,
        cart,
        confirmed
      }))
    }
  },
  data: function() {
    return {
      orders: [
        {
          id: 1,
          user: "Ahmed",
          cart: [
            { id: 1, name: 'Pizza', count: 2},
            { id: 2, name: 'Kebab', count: 1},
            { id: 3, name: 'Wurstel', count: 1},
            ],
          confirmed: false
        }
      ]
    }
  },
  components: {
    NodePanel,
    ApiSimulation
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
