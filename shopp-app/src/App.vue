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
              <td><button @click="p.quantity = p.quantity + 1">Dodaj</button></td>
              <td><button @click="p.quantity = p.quantity - 1">Usuń</button></td>
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
      <p>Razem: </p>
  </div>
</body>
</template>

<style scoped>
table, th, td {
  border:1px solid black;
  text-align:center
}
</style>

<script setup>
    import products from './data.js'
    import { computed, ref } from 'vue'
        const filteredProducts = 
      computed(() => products.value.filter(p => p.quantity > 0))
</script>