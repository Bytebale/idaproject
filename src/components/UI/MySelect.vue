<template>
  <select v-model="modelValue" @change="changeOption" class="mySelect">
    <option disabled value="">Сортировать</option>
    <option v-for="option in options"
            :key="option.value"
            :value="option.name"
    >
      {{option.name}}
    </option>
  </select>
</template>

<script>
export default {
  name: "MySelect",
  props: {
    modelValue: {
      type: String,
    },
    options: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    changeOption(event) {
      this.$emit('update:modelValue', event.target.value);
    }
  }
}
</script>

<style scoped>

.mySelect {
  float: right;
  background: #FFFEFB;
  box-shadow: 0px 20px 30px
  rgba(0, 0, 0, 0.04),
  0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
}
</style>