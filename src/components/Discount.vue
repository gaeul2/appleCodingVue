<script>
  import {onMounted} from "vue";

  export default  {
    name : 'Discount',
    data(){
      return {
      //   데이터 필요하면 여기에다 적으면 됨
      }
    },
    props: {
      discountNum : Number,
    }
  }
  //숙제1. 메인페이지 로드후부터 30%할인문구가 1초마다 1%씩 감소

  //숙제2 . 모달창의 input안에 2를 기입했을때 알림창 띄우기(힌트 : 업데이트되기전 beforeUpdate?
</script>

<template>
  <div class="discount">
    <h4>지금 결제하면 {{ discountNum }}%할인!!</h4>
  </div>
</template>

<style scoped>

</style>