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

  },
  methods : {
    modalPop(){
      this.$emit('openModal', this.product.id)
    }
  }
}
</script>

<template>
  <div>
    <img :src="product.image"/>
<!--    방법1. $emit에서 product.id를 openModal로 보내고 그걸 부모가 꺼내쓰기 -->
<!--    <h4 @click="$emit('openModal', product.id)"> {{number}} 번째 매물 : {{product.title}} </h4>-->
<!--    방법2. 부모한테 받은 데이터로 사용하기-->
<!--    <h4 @click="$emit('openModal')"> {{number}} 번째 매물 : {{product.title}} </h4>-->
<!--    만약에 $emit이 길어. 그럼 함수화해서 쓰기 아래 methods에-->
    <h4 @click="modalPop()"> {{number}} 번째 매물 : {{product.title}} </h4>
    <p>가격 : {{product.price}}원</p>
    <button @click="app.methods.addNumber(number)">허위매물신고</button>
    <span>신고수 : {{product.reportCnt}}</span>
  </div>

</template>

<style scoped>

</style>