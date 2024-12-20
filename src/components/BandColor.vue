<template>
  <div class="product__colors">
    <p>Band Color:</p>
    <div id="color-options" class="product__colors-options d-flex gap-3">
      <button v-for="color in colors" :key="color.name" class="product__colors-button rounded-circle" :style="{ backgroundColor: color.code, borderColor: color.code }" :class="{ 'active-color': selectedColor === color.name }" @click="changeThumbnail(color.imgSrc, color.name, color.code)"></button>
    </div>
  </div>
</template>

<script>
import lightBlue from "../assets/img/light-blue.png";
import black from "../assets/img/black.png";
import blue from "../assets/img/blue.png";
import cyan from "../assets/img/cyan.png";

export default {
  name: "BandColor",
  data() {
    return {
      colors: [
        { name: "Light Blue", code: "#816bff", imgSrc: lightBlue },
        { name: "Black", code: "#1fcec9", imgSrc: black },
        { name: "Blue", code: "#4b97d3", imgSrc: blue },
        { name: "Cyan", code: "#3b4747", imgSrc: cyan },
      ],
      selectedColor: "", // Track the selected color
    };
  },
  methods: {
    changeThumbnail(imgSrc, colorName, colorCode) {
      this.selectedColor = colorName;
      this.$emit("update-thumbnail", imgSrc, colorName);
      this.$emit("update-color", colorCode);
    },
  },
};
</script>

<style scoped></style>
