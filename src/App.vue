<template >
  <div class="App">
    <div class="sidebar">
      <product-form
          @create="addProduct"
      />
    </div>
    <div class="body">
      <my-select
          v-model="selectedSort"
          :options="sortOptions"
      />
      <product-list
          :products="sortedList"
          @remove="removeProduct"
      />
    </div>
  </div>
</template>

<!--https://upload.wikimedia.org/wikipedia/commons/6/6b/Icecat1-300x300.svg-->


<script>
import productList from "@/components/productList";
import productForm from "@/components/productForm";
import MySelect from "@/components/UI/MySelect";
export default {
  components: {
    MySelect,
    productList, productForm
  },
  data() {
   return {
     products: [],
     selectedSort: '',
     sortOptions: [
       {value: 'title', name: 'По наименованию'},
       {value: 'price', name: 'По цене min'},
       {value: 'price', name: 'По цене max'}
     ],
    }
  },
  methods: {
    addProduct(product) {
      this.products.push(product);
    },
    removeProduct(product) {
      this.products = this.products.filter(p => p.id !== product.id)
    },
  },
  computed: {
    sortedList () {
      console.log(this.selectedSort);
      switch(this.selectedSort){
        case 'По наименованию': return this.products.sort(sortByTitle);
        case 'По цене min': return this.products.sort(sortByPriceMin);
        case 'По цене max': return this.products.sort(sortByPriceMax);
        default: return this.products;
      }
    }
  }
}
let sortByTitle = function (d1, d2) {return (d1.title.toLowerCase() > d2.title.toLowerCase()) ? 1 : -1;};
let sortByPriceMin = function (d1, d2) { return (d1.price > d2.price) ? 1 : -1; };
let sortByPriceMax = function (d1, d2) { return (d1.price < d2.price) ? 1 : -1; };
</script>

<style>
* {
  margin: 0;
  box-sizing: border-box;
}

.App {
  display: grid;
  grid-template-columns: 330px 75%;
  gap: 1rem;
  margin: 15px;
}
</style>