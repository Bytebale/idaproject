<template>
  <div class="sidebar">
    <h1>Добавление товара</h1>
    <form @submit.prevent class="myForm">
      <div>
        Наименование товара
        <div style="color: red">*</div>
      </div>
      <input
          placeholder="Введите наименование товара"
          v-model="product.title"
          type="text"
      />
      <div>Описание товара </div>
      <input
          v-model="product.body"
          placeholder="Введите описание товара"
          class="productDescription"
          type="text"
      />
      <div>
        Ссылка на изображение
        <div style="color: red">*</div>
      </div>
      <input
          placeholder="Введите ссылку"
          v-model="product.link"
          type="url"
      />
      <div>
        Цена товара
        <div style="color: red">*</div>
      </div>
      <input
          placeholder="Введите цену"
          v-model="product.price"
          type="number"
      />
      <div>
        <button
            v-if="!product.link || !product.title || !product.price "
            disabled
            class="btn"
        >
          Добавить товар
        </button>
        <button v-else="" class="btn_active" @click="addProduct" >
           Добавить товар
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      product: {
        title:'',
        body:'',
        link:'',
        price: '',
      }
    }
  },
  methods: {
    addProduct() {
      this.product.id = Date.now();
      this.$emit('create', this.product);
      this.product = {
        title: '',
        body: '',
        link: '',
        price: '',
      }
    }
  }
}
</script>

<style scoped>
.myForm {
  position: center;
  padding: 15px;
  width: 332px;
  height: 440px;

  background: #FFFEFB;
  box-shadow: 0px 20px 30px
  rgba(0, 0, 0, 0.04),
  0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
}

.myForm > input {
  width: 284px;
  height: 36px;
  display: flex;
  margin: 5px 5px;

  background: #FFFEFB;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
}
.myForm > input.productDescription {
  height: 108px;
}
placeholder {
  position: fixed;
  margin-top: 0;

  font-family: 'Source Sans Pro';
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 15px;
  color: #B4B4B4;
}
.myForm >div {
  display: flex;
}

.btn {
  width: 284px;
  height: 36px;
  display: flex;
  margin: 15px 5px;
  padding: 5px;
  justify-content: center;
  background: #EEEEEE;
  border-radius: 10px;

  font-family: 'Inter';
  font-style: normal;
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  text-align: center;
  letter-spacing: -0.02em;
  color: #B4B4B4;
}

.btn_active {
  width: 284px;
  height: 36px;
  display: flex;
  margin: 15px 5px;
  padding: 5px;
  justify-content: center;
  background: #7BAE73;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 10px;

  font-family: 'Inter';
  font-style: normal;
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  color: #FFFFFF;
}

</style>