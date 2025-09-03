<script>
import app from "@/App.vue";

export default {
  name: "ProductList",
  computed: {
    app() {
      return app
    }
  },
  props : {
    product : Object,
    number : Number,

  }
}
</script>

<template>
  <div>
    <img :src="product.image"/>
    <h4 @click="app.methods.showModal(number)"> {{number}} 번째 매물 : {{product.title}} </h4>
    <p>가격 : {{product.price}}원</p>
    <button @click="app.methods.addNumber(number)">허위매물신고</button>
    <span>신고수 : {{product.reportCnt}}</span>
  </div>

</template>

<style scoped>

</style>