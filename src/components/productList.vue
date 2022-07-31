<template>
  <div class="productCards" >
      <product-item
          v-for="product in products"
          :product="product"
          :key="product.id"
          @remove="$emit('remove', product)"
      />
  </div>
</template>

<script>
import ProductItem from "@/components/ProductItem";
export default {
  components: {ProductItem},
  props: {
    products: {
      type: Array,
      required: true,
    }
  }
}
</script>

<style scoped>
.productCards {
  display: grid;
  margin-top: 25px;
  justify-content: start;
  grid-template-columns: repeat(3, 0.25fr);
  grid-gap: 1rem;
  grid-auto-rows: minmax(100px, auto);
}
</style>