<template>
  <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
  <div>
    원룸샵
    <h4 :class="클래스" :style="스타일">{{ products[0].title }}</h4>
<!--    <p>{{ price1 }} 만원</p>-->
    <p>{{ products[0].price }} 만원</p>
  </div>
  <div>
    <h4>{{ products[1].title }}</h4>
<!--    <p>{{ price2 }} 만원</p>-->
    <p>{{ products[1].price }} 만원</p>
  </div>
  <div>
    <h4>{{ products[2].title }}</h4>
    <p>{{ price3 }} 만원</p>
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
      클래스 : 'test-class',
      products : [ {'title' : '역삼동원룸', 'price' : 60}, {'title' :'천호동원룸', 'price' : 70}, {'title' :'마포구원룸', 'price' : 80}],
      price3: 80,
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
</style>