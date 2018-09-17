<template>
  <div id="app">
    <h2>Lojinha</h2>

    <p>Estoque de Produtos</p>

    <ul>
      <transition-group name="fade">
        <li v-for="(product, key) in products" v-bind:key="product.id">
          <input type="number" v-model.number="product.quantity" min="0">
          <span>{{ product.name }}</span>
          <button @click="remove(key)">Remover</button>
          <button @click="adicionarItem(product)" v-bind:disabled="product.quantity === 0">Adicionar</button>
        </li>
      </transition-group>
    </ul>

    <p>
      Total Quantidade Items: 
      <span v-if="totalQuantity > 0">{{ totalQuantity }}</span>
      <span v-else>Sem Estoque</span>
    </p>

    

    <p>
      <strong>Total items: </strong>
      <span>{{ cart.length }}</span>
    </p>
  </div>
</template>

<script>
//https://api.myjson.com/bins/nsvk0
export default {
  name: 'app',
  data () {
    return {
      products: [],
      cart: []
    }
  },
  computed: {
    totalQuantity() {
      return this.products.reduce((sum, product) => {
        return sum + parseFloat(product.quantity);
      }, 0);
    }
  },
  created() {
    fetch("https://api.myjson.com/bins/74l63")
    .then((response) => response.json())
    .then(json => {
      this.products = json.products;
    })
  },
  methods: {
    adicionarItem(productItem) {
      if (productItem.quantity > 0) {
        this.cart.push(productItem);
        productItem.quantity--;
      }
    },
    remove(itemIndex) {
      console.info(itemIndex)
      this.products.splice(itemIndex, 1);
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: block;
  margin: 0 10px;
  text-align: left;
}

a {
  color: #42b983;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
