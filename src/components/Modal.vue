<script>
import Discount from "@/components/Discount.vue";
import {productInfo} from "@/data/oneroom.js";
import app from "@/App.vue";
import {onBeforeUpdate} from "vue";

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
  },
  data(){
    return {
      month : 1,
      originPrice : this.products[this.number].price
    }
  },
  methods : {
    sendMonth(month){
      this.month = month;
      this.$emit('dataMonth-idx', {month : month, idx : this.number, oriPrice : this.originPrice})
    }
  },
  watch : {
    month(a,b){
      console.log( typeof(a));
      if ( a >= 13){
        alert("13개월 이상 입력하실 수 없습니다.");
        this.month = 1;

      }

      if ( !Number(a.trim()) ){
        alert("숫자를 입력해 주세요");
        this.month = 1;
      }
    }
  },
  updated(){
    console.log(this.month)
    if (this.month === '2' ){
      alert("2개월은 선택하실수 없습니다.\n1개월 혹은 3개월이상으로 입력해주세요.");
      this.month = 1;
    }
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

<!--      <input @input="month = $event.target.value">-->
<!--      <input v-model.number="month">-->
<!--      <textarea v-model="month"></textarea>-->
<!--      <select v-model="month">-->
<!--        <option>1</option>-->
<!--        <option>2</option>-->
<!--        <option>3</option>-->
<!--      </select>-->
<!--      <input type="checkbox" v-model="month"/>-->
            <input @input="sendMonth($event.target.value)">
      <p> {{ month }}개월 선택함 : {{ products[number].price}}원</p>
<!--      <p> {{ month }}개월 선택함 : {{ products[number].price * month}}원</p>-->

      <Discount/>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<style scoped>

</style>