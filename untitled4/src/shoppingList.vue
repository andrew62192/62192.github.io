<template>
  <div>
    <h1>泡麵價格商品網站</h1>

    <h2>輸入商品資訊</h2>
    <form id="productForm" @submit.prevent="addProduct">
      <label htmlFor="date">日期:</label>
      <input type="date" id="date" v-model="newProduct.date" required><br>

      <label htmlFor="productName">商品名稱:</label>
      <input type="text" id="productName" v-model="newProduct.name" required><br>

      <label htmlFor="price">商品價格:</label>
      <input type="number" id="price" v-model="newProduct.price" required><br>

      <button type="submit">新增商品</button>
    </form>

    <h2>物價變化</h2>
    <table>
      <tr>
        <th>日期</th>
        <th>商品名稱</th>
        <th>商品價格</th>
      </tr>
      <tr v-for="product in products" :key="product.date">
        <td>{{ product.date }}</td>
        <td>{{ product.name }}</td>
        <td>{{ product.price }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [],
      newProduct: {
        date: '',
        name: '',
        price: ''
      }
    };
  },
  methods: {
    addProduct() {
      this.products.push({...this.newProduct});
      this.clearForm();
    },
    clearForm() {
      this.newProduct.date = '';
      this.newProduct.name = '';
      this.newProduct.price = '';
    }
  }
};
</script>

<style scoped>
table {
  border-collapse: collapse;
}

table,
th,
td {
  border: 1px solid black;
}
</style>
