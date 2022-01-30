<template><!-- 여기에 HTML-->

  <!---->
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{menu}} </a><!--Vue의 for문-->
    
    <a v-for="(menu,i) in menus" :key="i">{{menu}} {{i}}</a><!--두가지 변수가 들어갈 시 두번째는 인덱스 번호가 됨-->
  </div>
  <div>
    <h4> {{array}}리스트</h4>
    <p>{{playlist}} 만원</p>
    <button @mousewheel="increase">허위매물 신고</button> <span>신고 수 : {{warning[0]}} 위험도 : {{Math.floor(warning[1])}}</span><!--v-on을 @로 대체 가능-->
    <!--@ 누르고 넣을 함수 넣기-->
    

    <!--babel이란? 자바스크립트를 해석해주는 도구-->
  </div>

    <div v-for="building in buildings" :key="building">
      이름 : {{building}}
      <p></p>


<!--어...그런데 vue와 스프링을 어떻게 연결하지...?-->
    </div>

  <div>
    <h4>매물갯수</h4>
    <p>{{latest}}개</p>
  </div>
</template>

<script> //여기에  JS


export default {
  name: 'App',
  data(){
    return{
      warning : [0,0],
      playlist : 60,
      latest : 30,
      array : ['여기','저기','거기'],
      menus : ['Home','Shop','About'],
      buildings : ['강남','서초','역삼']
    }
  },
  methods :{//method는 funtion의 모음 같은 느낌
    //funtion이름(){실행할 코드}
    increase(){
      this.warning[0] += 1;      //data 안의 변수를 불러올땐 this
      if(this.warning[0] > 10){
        this.warning[1] += 0.1;
      }
      if(this.warning[1] > 100){
        this.warning[1] = 100;
      }
    }
  },
  components: {
    
  }
}
</script>

<style>/* 여기다 CSS*/
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}

.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a{
  color: white;
  padding: 15px;

}
</style>
