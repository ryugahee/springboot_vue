<template>
  <div class="card shadow-sm">
    <!--  그림 사이즈 통일  -->
    <span class="img" :style="{backgroundImage: `url(${item.imgPath})`}"/>
    <div class="card-body">
      <p class="card-text">{{ item.name }}</p>
      <div class="d-flex justify-content-between align-items-center">
        <button class="btn btn-primary">구입하기</button>
        <small class="price text-body-secondary">
          <!--  숫자에 콤마 추가  -->
          {{ lib.getNumberFormatted(item.price) }}원
        </small>
        <small class="discount badge bg-danger">
          <!--  할인율  -->
          {{ item.discountPer }}%
        </small>
        <small class="discount text-danger text-body-secondary">
          <!--  할인가  -->
          {{lib.getNumberFormatted(item.price - (item.price * item.discountPer / 100)) }}원
        </small>
      </div>
    </div>
  </div>
</template>

<script>
import lib from "@/scripts/lib";

export default {
  name: "Card",
  props: {
    item: Object
  },
  setup() {
    return {lib}
  },
}
</script>

<style scoped>
.card .img {
  display: inline-block;
  width: 100%;
  height: 350px;
  background-size: cover;
  background-position: center;
}
.card .card-body .price {
  text-decoration: line-through;
}
</style>