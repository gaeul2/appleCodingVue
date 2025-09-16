<template>

  <transition name="fade">
    <modal1 @closeModal="hideModal()" :products="products" :number="number" :modalVisible="modalVisible"
            @dataMonth-idx="multiply($event)"/>
  </transition>


  <div class="menu" :class="{ end : modalVisible }">
    <a v-for="(menu, i) in 메뉴들" :key="menu">{{i+1}}번째 메뉴 : {{ menu }}</a>
  </div>

  원룸샵
  <Discount/>

  <button @click="priceSort">가격순정렬</button>
  <button @click="priceSortDesc">가격역순정렬</button>
  <button @click="priceSortWord">가나다순정렬</button>
  <button @click="sortBack">되돌리기</button>

   <!-- 방법1. 자식 -> $emit('작명', 데이터) -> 부모 ($event)로 꺼내 쓸수 있음.-->
<!--  <Card @openModal="showModal($event)" v-for="(product,i) in products" :key="i" :product="product" :number="i"/>-->

<!--  방법2. 여기서 그냥 i 보내.-->
  <Card @openModal="showModal($event)" v-for="(product,i) in products" :key="i" :product="product" :number="i"/>




<!--  <Card :products="products" />-->
</template>

<script>
//export dafault로 가져온건 변수명 굳이 안맞춰도 됨
// import data from "@/data/oneroom.js";
import {productInfo} from "@/data/oneroom.js";
import Discount from "@/components/Discount.vue";
import Modal from "@/components/Modal.vue";
import Card from "@/components/Card.vue";

export default {
  name : 'App',
  data(){
    return {
      스타일 : 'color : blue',
      검정 : 'color:black',
      클래스 : 'test-class',
      // products : [ {'title' : '역삼동원룸', 'price' : 60, '신고수': 0}, {'title' :'천호동원룸', 'price' : 70, '신고수': 0}, {'title' :'마포구원룸', 'price' : 80, '신고수': 0 }],
      // products : data,
      products : [...productInfo],
      oriProducts : productInfo,
      메뉴들 : ['Home', 'Shop', 'About'],
      modalVisible : false,
      modalContent : '',
      modalTitle : '',
      number : 0,
    }
  },
  methods : {
    addNumber(index){
      this.products[index].reportCnt++;
      alert((index + 1)  + "번째 매물이 신고되었습니다.");
    },
    showModal(index){
      this.modalVisible = true;
      this.modalContent = productInfo[index].content;
      this.modalTitle = productInfo[index].title;
      this.number = index;
    },
    hideModal(){
      this.modalVisible = false;
      this.modalContent = '';
      this.modalTitle = '';
      this.number = 0;
    },
    multiply(test){
      this.products[test.idx].price = test.oriPrice * test.month;
    },
    priceSort(){
      this.products.sort(function(a, b){
        return a.price - b.price
      });
    },
    sortBack(){
      this.products = [...this.oriProducts]
    },
    priceSortWord(){
      this.products.sort(function(a,b){
        return a.title.localeCompare(b.title)
      });
    },
    priceSortDesc(){
      this.products.sort(function (a,b){
        return b.price - a.price
      })

    }

  },
  components : {
    Card,
    Discount,
    modal1 : Modal,
  }
}
</script>

<style>
  body{
    margin : 0
  }
  div{
    box-sizing: border-box;
  }
  .discount{
    background : #eee;
    padding:10px;
    margin:10px;
    border-radius: 5px;
  }
  .black-bg{
    width: 100%; height: 100%;
    background: rgba(0,0,0,0.5);
    position: fixed; padding: 20px;
  }
  .white-bg{
    width: 100%; background: white;
    border-radius: 8px;
    position: fixed; padding: 20px;
  }
  .room-img{
    width: 100%;
    margin-top: 40px;
  }
  #app{
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align:center;
    color:#2c3e50;
  }

  .menu{
    background : darkslateblue;
    padding : 15px;
    border-radius: 5px;
  }
  .menu a{
    color : white;
    padding : 10px;
  }

  .start{
    opacity: 0;
    transition : all 5s;
  }
  .end {
    opacity : 1;
  }

  .fade-enter-from {
    opacity: 0;
  }
  .fade-enter-active {
    transition: all 0.5s;
  }
  .fade-enter-to {
    opacity: 1;
  }

  .fade-leave-from { opacity: 1;}
  .fade-leave-active { transition: all 0.5s}
  .fade-leave-to {opacity: 0;}
</style>