<template>
<body> 
  <div>
      <h1>Lista produktów</h1>
      <table>
          <tr>
            <th>Nazwa produktu</th>
            <th>Cena</th>
            <th>Dodaj do koszyka</th>
          </tr>
          <tr v-for="p in products" :key="p.id">
              <td>{{ p.name }}</td>
              <td>{{ p.price }}</td>
              <td><button @click="basket_products.push({ id: index, name: p.name, price: p.price})">Dodaj</button></td>
          </tr>
      </table>
  </div>
  <div>
      <h1>Koszyk</h1>
      <table>
          <tr>
            <th>Nazwa produktu</th>
            <th>Cena</th>
          </tr>
          <tr v-for="p in basket_products" :key="p.id">
              <td>{{ p.name }}</td>
              <td>{{ p.price }}</td>
          </tr>
      </table>
      <p><button @click="basket_products.pop()">Usuń</button></p>
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
    import basket_products from './basket.js'
</script>