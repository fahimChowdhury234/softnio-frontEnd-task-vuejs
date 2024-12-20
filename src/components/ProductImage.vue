<template>
  <div class="col-md-6 product__image">
    <img id="main-thumbnail" :src="imageSrc" alt="Smart Watch" class="product__image-thumbnail img-fluid rounded border" />
  </div>
</template>

<script>
export default {
  name: "ProductImage",
  props: {
    imageSrc: {
      type: String,
      default: "../assets/img/light-blue.png",
    },
  },
};
</script>

<style scoped></style>
