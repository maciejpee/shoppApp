<template>
<body> 
  <div>
      <h1>Lista produktów</h1>
      <table>
          <tr>
            <th>Nazwa produktu</th>
            <th>Cena</th>
            <th>Dodaj do koszyka</th>
            <th>Usuń z koszyka</th>
          </tr>
          <tr v-for="p in products" :key="p.id">
              <td>{{ p.name }}</td>
              <td>{{ p.price }}</td>
              <td><button @click="p.quantity = addProduct(p.quantity, p.price)">Dodaj</button></td>
              <td><button :disabled="blocked" @click="p.quantity = removeProduct(p.quantity, p.price)">Usuń</button></td>
          </tr>
      </table>
  </div>
  <div>
      <h1>Koszyk</h1>
      <table>
          <tr>
            <th>Nazwa produktu</th>
            <th>Cena</th>
            <th>Ilość</th>
            <th>Razem</th>
          </tr>
          <tr v-for="p in filteredProducts" :key="p.id">
              <td>{{ p.name }}</td>
              <td>{{ p.price }}</td>
              <td>{{ p.quantity }}</td>
              <td>{{ p.quantity*p.price }}</td>
          </tr>
      </table>
      <p>Wartość koszyka: {{ totalValue }}</p>
  </div>
</body>
</template>

<script setup>
    import products from './data.js'
    import { computed, ref } from 'vue'
    const filteredProducts = computed(() => products.value.filter(p => p.quantity > 0))
    const blocked = ref(false)
    const totalValue = ref(0)

    function addProduct (quantity, price) {
      quantity = quantity + 1
      totalValue.value = totalValue.value + price
      return quantity
    }


    function removeProduct (quantity, price) {
      quantity = quantity - 1
      if (quantity < 0) { blocked = true }
      totalValue.value = totalValue.value - price
      return quantity
    }

</script>

<style scoped>
table, th, td {
  border:1px solid black;
  text-align:center
}
</style>

