<template>
  <div class="productCard">
    <div class="delete__btn">
      <button @click="$emit('remove', product)">X</button>
    </div>
    <div
        class="prodImage" :style="{backgroundImage: 'url(' +product.link.valueOf()+ ')' }">
    </div>
    <div>
      <h3>{{product.title}}</h3>
    </div>
    <div>
      <p> {{product.body}} </p>
    </div>
    <div>
      <strong>{{ product.price.toLocaleString('ru-RU')}} Руб. </strong>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    product: {
      type: Object,
      required: true,
    }
  }
}
</script>

<style scoped>
.productCard {
  display: grid;
  width: 332px;
  height: 423px;

  background: #FFFEFB;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
}

.productCard:hover {
  width: 345px;
  height: 450px;
  transition: all;
}

.prodImage {
  position: relative;
  width: 100%;
  height: 200px;
  border-radius: 4px 4px 0px 0px;
  background-repeat: no-repeat;
  background-size: 300px 200px;
}

.delete__btn{
  text-align: end;
}
.delete__btn > button {
  width: 20px;
  height: 20px;

  color: rgba(0,0,0,0.1);
  border-color: transparent;
  border-radius: 10px;
}
.delete__btn > button:hover {
  width: 32px;
  height: 32px;
  color: rgba(0,0,0,0.5);
  background: #FF8484;
  border-radius: 20px;
}
</style>