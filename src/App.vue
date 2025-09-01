<template>
  <div class="black-bg" v-if="modalVisible === true">
    <div class="white-bg">
<!--      <h4>{{ modalTitle }}</h4>-->
<!--      <p>{{ modalContent }}</p>-->
      <h4>{{ products[number].title }}</h4>
      <div >
        <img :src="products[number].image" style="width: 80%">
      </div>
      <p>{{ products[number].content }}</p>
      <p>가격 : {{ products[number].price }}</p>
      <button @click="hideModal">닫기</button>
    </div>
  </div>


  <div class="menu">
    <a v-for="(menu, i) in 메뉴들" :key="menu">{{i+1}}번째 메뉴 : {{ menu }}</a>
  </div>
  원룸샵
  <div v-for="(product, i) in products" :key="product">
<!--    <img :src="'./assets/images/room',i,'.jpg'" class="room-img"/>-->
    <img :src="product.image" class="room-img"/>
    <h4 @click="showModal(i)">{{i + 1 }}번째 매물 : {{product.title}}</h4>
    <p :style="스타일">{{product.price}} <span :style="검정">만원</span></p>
    <button @click="addNumber(i)">허위매물신고</button> <span>신고수 : {{ products[i].reportCnt }}</span>
  </div>
</template>

<script>
//export dafault로 가져온건 변수명 굳이 안맞춰도 됨
// import data from "@/data/oneroom.js";
import {productInfo} from "@/data/oneroom.js";

export default {
  name : 'App',
  data(){
    return {
      스타일 : 'color : blue',
      검정 : 'color:black',
      클래스 : 'test-class',
      // products : [ {'title' : '역삼동원룸', 'price' : 60, '신고수': 0}, {'title' :'천호동원룸', 'price' : 70, '신고수': 0}, {'title' :'마포구원룸', 'price' : 80, '신고수': 0 }],
      // products : data,
      products : productInfo,
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
    }
  },
  components : {
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
</style>