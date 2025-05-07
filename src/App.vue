<template>
  <!--
  modal_open이 tru면 보여주기 아니면 안보여주기
  v-on = @ 같은 말
  -->
  <!-- vue 주요사항 잘 만들었어도 이미지 소스등 데이터가 없다면 렌더링 되지 않음음-->
  <div class="black_bg" v-if=" modal_open == true" @click="modal_open = false">
    <div class="white_bg">
        <h4>상세페이지임</h4>
        <p>상세페이지내용</p>
        <button @click="modal_open = false">닫기</button>
    </div>
  </div>
  <div class="menu">
    <a v-for="(a,i) in menus" :key="i">{{ a }}</a>
    
  </div>

  <div v-for="(content,i) in onerooms" :key="i">
    <img class="room" :src="get_image(i)">
    <h4 @click="modal_open = true">{{content.title}}</h4>
    <!-- DAta[배열].원하는 데이터 이름름-->
    <p>{{content.price}}</p>
    <button v-on:click="report_plus(i)">허위매물신고</button> <span>신고수 : {{report[i]}}</span>
  </div>

</template>

<script>
//export {작명}
//import {작명} from '주소';

//exprot  default 이름
//import 작명 from '주소'\

import data from './data.js';

export default {
  name: 'App',
  data(){
    const products = [['역삼동원룸','60'],['천호동원룸','50'],['마포구원룸','40']];
      return{
        onerooms : data,
        modal_open : false,
        products,
        menus : ['Home','Shop','About'],
        report : new Array(products.length).fill(0)
      }
    },
  methods :{
    get_image(index){
      return require('@/assets/room'+index+'.jpg');
    },
    report_plus(index){
      this.report[index]++;
    }
  },
  components: {
    
  }
}
</script>

<style>
#app{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing:  antialiased;
  -moz-osx-font-smoothis: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu{
  background:darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
}
.room{
  width: 500px;
}
.black_bg{ position: fixed; padding: 20px; width: 100%; height: 100%; box-sizing: border-box; background:rgba(0,0,0,.5);}
.white_bg{ background:white; border-radius: 8px; padding: 20px;}
</style>
