<template>
  <div class="black-bg" v-if="modalVisible === true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="hideModal">닫기</button>
    </div>
  </div>


  <div class="menu">
    <a v-for="(menu, i) in 메뉴들" :key="menu">{{i+1}}번째 메뉴 : {{ menu }}</a>
  </div>
  원룸샵
  <div v-for="(product, i) in products" :key="product">
<!--    <img src="./assets/images/room{{i}}.jpg" class="room-img"/>-->
    <img src="./assets/images/room0.jpg" class="room-img"/>
    <h4 @click="showModal">{{i + 1 }}번째 매물 : {{product.title}}</h4>
    <p :style="스타일">{{product.price}} <span :style="검정">만원</span></p>
    <button @click="addNumber(i)">허위매물신고</button> <span>신고수 : {{ products[i].신고수 }}</span>
  </div>
<!--  <div>-->
<!--    <h4>{{products[0].title}}</h4>-->
<!--    <p :style="스타일">{{products[0].price}} <span :style="검정">만원</span></p>-->
<!--&lt;!&ndash;    <button v-on:click="">허위매물신고</button> <span>신고수 : 0</span>&ndash;&gt;-->
<!--    <button @click="addNumber">허위매물신고</button> <span>신고수 : {{ products[0].신고수 }}</span>-->
<!--  </div>-->
<!--  <div>-->
<!--    <h4>{{products[1].title}}</h4>-->
<!--    <p :style="스타일">{{products[1].price}} <span :style="검정">만원</span></p>-->
<!--    <button @click="addNumber">허위매물신고</button> <span>신고수 : {{ products[1].신고수}}</span>-->
<!--  </div>-->
<!--  <div>-->
<!--    <h4>{{products[2].title}}</h4>-->
<!--    <p :style="스타일">{{products[2].price}} <span :style="검정">만원</span></p>-->
<!--    <button @click="addNumber">허위매물신고</button> <span>신고수 : {{ products[2].신고수}}</span>-->
<!--  </div>-->
</template>

<script>
export default {
  name : 'App',
  data(){
    return {
      price1 : 60,
      price2 : 70,
      스타일 : 'color : blue',
      검정 : 'color:black',
      클래스 : 'test-class',
      products : [ {'title' : '역삼동원룸', 'price' : 60, '신고수': 0}, {'title' :'천호동원룸', 'price' : 70, '신고수': 0}, {'title' :'마포구원룸', 'price' : 80, '신고수': 0 }],
      price3: 80,
      메뉴들 : ['Home', 'Shop', 'About'],
      modalVisible : false,
    }
  },
  methods : {
    addNumber(index){
      this.products[index].신고수++;
      alert((index + 1)  + "번째 매물이 신고되었습니다.");
    },
    showModal(){
      this.modalVisible = true;
    },
    hideModal(){
      this.modalVisible = false;
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