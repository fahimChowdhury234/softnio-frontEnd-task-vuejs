<template>
  <div class="product__quantity d-flex align-items-center mb-3">
    <div class="product__quantity__box d-flex align-items-center">
      <button class="product__quantity-decrement" @click="decrementQuantity">
        <svg width="14" height="2" viewBox="0 0 14 2" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M13.1607 1.675H1.03926C0.825977 1.675 0.642318 1.60391 0.488281 1.46172C0.346094 1.30768 0.275 1.12402 0.275 0.910742C0.275 0.70931 0.346094 0.5375 0.488281 0.395312C0.642318 0.241276 0.825977 0.164257 1.03926 0.164257H13.1607C13.374 0.164257 13.5518 0.241276 13.6939 0.395312C13.848 0.5375 13.925 0.70931 13.925 0.910742C13.925 1.12402 13.848 1.30768 13.6939 1.46172C13.5518 1.60391 13.374 1.675 13.1607 1.675Z" fill="#8091A7" />
        </svg>
      </button>
      <input id="quantity" type="number" v-model="quantity" min="0" class="product__quantity-input text-center" />
      <button class="product__quantity-increment" @click="incrementQuantity">
        <svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path
            d="M13.1607 6.16426C13.374 6.16426 13.5518 6.24128 13.6939 6.39531C13.848 6.5375 13.925 6.70931 13.925 6.91074C13.925 7.12402 13.848 7.30768 13.6939 7.46172C13.5518 7.60391 13.374 7.675 13.1607 7.675H7.86426V12.9893C7.86426 13.1907 7.78724 13.3684 7.6332 13.5225C7.49102 13.6646 7.31328 13.7357 7.1 13.7357C6.88672 13.7357 6.70306 13.6646 6.54902 13.5225C6.40684 13.3684 6.33574 13.1907 6.33574 12.9893V7.675H1.03926C0.825977 7.675 0.642318 7.60391 0.488281 7.46172C0.346094 7.30768 0.275 7.12402 0.275 6.91074C0.275 6.70931 0.346094 6.5375 0.488281 6.39531C0.642318 6.24128 0.825977 6.16426 1.03926 6.16426H6.33574V0.849999C6.33574 0.636718 6.40684 0.458984 6.54902 0.316796C6.70306 0.16276 6.88672 0.0857416 7.1 0.0857416C7.31328 0.0857416 7.49102 0.16276 7.6332 0.316796C7.78724 0.458984 7.86426 0.636718 7.86426 0.849999V6.16426H13.1607Z"
            fill="#8091A7"
          />
        </svg>
      </button>
    </div>
    <button class="product__add-cart d-flex align-items-center gap-2" @click="addToCart">
      <span>Add to Cart</span>
    </button>
    <div class="product__heart">heart</div>
  </div>
</template>

<script>
export default {
  name: "QuantityControl",
  data() {
    return {
      quantity: 0,
    };
  },
  methods: {
    incrementQuantity() {
      this.quantity++;
    },
    decrementQuantity() {
      if (this.quantity > 0) this.quantity--;
    },
    addToCart() {
      this.$emit("add-to-cart", this.quantity);
    },
  },
};
</script>

<style scoped></style>
