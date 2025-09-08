<script>
import Discount from "@/components/Discount.vue";
import {productInfo} from "@/data/oneroom.js";
import app from "@/App.vue";

export default {
  name: "Modal",
  computed: {
    app() {
      return app
    }
  },
  components: {Discount},
  props:{
    products : Object,
    number : Number,
    modalVisible : Boolean
  }
}
</script>

<template>
  <div class="black-bg" v-if="modalVisible === true">
    <div class="white-bg">
      <h4>{{ products[number].title }}</h4>
      <div >
        <img :src="products[number].image" style="width: 80%">
      </div>
      <p>{{ products[number].content }}</p>
      <p>가격 : {{ products[number].price }}원</p>
      <Discount/>
      <button @click="$emit('close')">닫기</button>
    </div>
  </div>
</template>

<style scoped>

</style>