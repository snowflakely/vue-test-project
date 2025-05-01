<template>
  <div class="menu">
    <a v-for="(a,i) in menus" :key="i">{{ a }}</a>
    
  </div>

  <div v-for="(content,i) in products" :key="i">
    <h4 class="red" :style="스타일">{{content[0]}}</h4>
    <p>{{ content[1]}}만원</p>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
      return{
        menus : ['Home','Shop','About'],
        products :[['역삼동원룸','60'],['천호동원룸','50'],['마포구원룸','40']]
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
