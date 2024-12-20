<template>
  <div class="product__sizes">
    <p>Wrist Size:</p>
    <div class="product__sizes-options d-flex gap-3">
      <button v-for="size in sizes" :key="size.name" class="product__sizes-button" :class="{ 'active-size': selectedSize === size.name }" @click="selectSize(size)">
        <b>{{ size.name }}</b> - ${{ size.price }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "WristSize",
  data() {
    return {
      sizes: [
        { name: "S", price: 69 },
        { name: "M", price: 79 },
        { name: "L", price: 89 },
        { name: "XL", price: 99 },
      ],
      selectedSize: "", // Store the selected size
    };
  },
  methods: {
    selectSize(size) {
      this.selectedSize = size.name; // Set the selected size
      this.$emit("update-size", `${size.name} - $${size.price}`);
    },
  },
};
</script>

<style scoped></style>
