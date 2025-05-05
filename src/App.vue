<template>
  <div class="menu">
    <a v-for="(a,i) in menus" :key="i">{{ a }}</a>
    
  </div>

  <div v-for="(content,i) in products" :key="i">
    <h4 class="red">{{content[0]}}</h4>
    <p>{{ content[1]}}만원</p>
    <button v-on:click="report_plus(i)">허위매물신고</button> <span>신고수 : {{report[i]}}</span>
  </div>

</template>

<script>



export default {
  name: 'App',
  data(){
    const products = [['역삼동원룸','60'],['천호동원룸','50'],['마포구원룸','40']];
      return{
        products,
        menus : ['Home','Shop','About'],
        report : new Array(products.length).fill(0)
      }
    },
  methods :{
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
</style>
