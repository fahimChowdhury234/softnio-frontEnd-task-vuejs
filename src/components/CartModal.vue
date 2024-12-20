<template>
  <div v-if="isCartVisible" class="cart-modal active">
    <div class="cart-modal__content">
      <h2 class="cart-modal__title">Your Cart</h2>
      <div class="cart-modal__items">
        <table class="table">
          <thead>
            <tr>
              <th>Item</th>
              <th>Color</th>
              <th>Size</th>
              <th>Quantity</th>
              <th>Total</th>
            </tr>
          </thead>
          <tbody>
            <tr v-if="cart.length === 0">
              <td colspan="4" class="text-center py-4">
                <p class="text-muted mb-0">No products available in cart</p>
              </td>
            </tr>
            <tr v-for="(item, index) in cart" :key="index">
              <td>
                <div class="d-flex align-items-center gap-2">
                  <img :src="item.image" :alt="item.title" class="cart-img" />
                  <span>{{ item.title }}</span>
                </div>
              </td>
              <td>{{ item.color }}</td>
              <td>{{ item.size }}</td>
              <td>{{ item.quantity }}</td>
              <td>${{ item.total.toFixed(2) }}</td>
            </tr>
          </tbody>
          <tfoot>
            <tr v-if="cart.length > 0">
              <td colspan="3"><strong>Totals:</strong></td>
              <td>
                <strong>{{ totalqnt }}</strong>
              </td>
              <td>
                <strong>${{ totalPrice.toFixed(2) }}</strong>
              </td>
            </tr>
          </tfoot>
        </table>
      </div>
      <div class="cart-footer">
        <button class="continue-shopping" @click="closeModal">Continue Shopping</button>
        <button class="checkout" @click="checkout">Checkout</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cart: {
      type: Array,
      required: true,
    },
    isCartVisible: {
      type: Boolean,
      required: true,
    },
  },
  computed: {
    totalPrice() {
      return this.cart.reduce((sum, item) => sum + item.total, 0);
    },
    totalqnt() {
      return this.cart.reduce((sum, item) => sum + item.quantity, 0); // Fix here: ensure it returns the total quantity
    },
  },
  methods: {
    closeModal() {
      this.$emit("close");
    },
    checkout() {
      this.$emit("checkout");
    },
  },
};
</script>

<style scoped></style>
