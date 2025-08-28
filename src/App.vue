<template>
  <div class="menu">
    <a v-for="(menu, i) in 메뉴들" :key="menu">{{i+1}}번째 메뉴 : {{ menu }}</a>
  </div>
  원룸샵
  <div v-for="title in products" :key="title">
    <h4>{{title.title}}</h4>
    <p :style="스타일">{{title.price}} <span :style="검정">만원</span></p>
  </div>
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
      products : [ {'title' : '역삼동원룸', 'price' : 60}, {'title' :'천호동원룸', 'price' : 70}, {'title' :'마포구원룸', 'price' : 80}],
      price3: 80,
      메뉴들 : ['Home', 'Shop', 'About']
    }
  },
  components : {
  }
}
</script>

<style>
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