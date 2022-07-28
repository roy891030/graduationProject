<template>
  <div id="app">
    <!-- 左半控制區 -->
    <div class="left">
      <!-- 左上的tab -->
      <b-card no-body class="left_top">
        <b-tabs card>
          <b-tab title="Icon" active>
            <!-- icon tab 中的調整項 -->
            <div class="setting">
              <label for="job" class="label_lt">行業</label>
              <b-form-select v-model="jobs_selected" :options="jobs" class="job"></b-form-select>
              <label for="sb-inline" class="label_lt">距離</label>
              <!-- 應該可以用相對位置等方式去調整pop的位置 -->
              <input class="form-range dis_range" id="range-1" v-model="range" type="range" min="300" max="1500"
                v-b-popover.hover.top="range"></input>
            </div>
            <!-- 圖例modal, 參數為行業 -->
            <Icon :jobType="jobs" :range="range" :select="jobs_selected" :returnmrt="returnmrt" :returnmarket="returnmarket" :returnmorto="returnmorto"/>
            </b-tab>
            <b-tab title=" 圖表">
              <b-card-text>圖表</b-card-text>
          </b-tab>
        </b-tabs>
      </b-card>
      <!-- 左下的tab -->
      <b-card no-body class="left_down">
        <b-tabs card>
          <b-tab title="評分" active>
            <span style="text-align:left; font-weight:bold; float:left">加權調整</span>
            <span style="text-align:left; font-weight:bold; float:right">評分</span><br><br>

            <label for="customRange1" class="form-label">{{score}}</label>
            <!--可任意調分-->
            <input type="range" class="form-range" id="customRange1" v-model="score"><br><br>
            <!-- 加權條整區modal, 參數為行業 -->
            <!-- <Score :jobType="jobs" :range="range"/> -->
          </b-tab>
          <b-tab title="總覽">
            <p>地點需求</p>
            <div style="height:300px; overflow:auto">
              <div class="tableline"></div>
              <p style="text-align:left">預估需求：</p>
              <p style="text-align:left">租金：</p>
              <p style="text-align:left">地址：</p>
              <p style="text-align:left">附近競爭者數：</p>
              <p style="text-align:left">附近市場數：</p>
              <p style="text-align:left">附近捷運站數：</p>
              <p style="text-align:left">區域平均租金：</p>
            </div>
            <!-- 參數...好像...很多... -->
            <!-- <Overview :jobType="jobs" :range="range"/> -->
          </b-tab>
        </b-tabs>
      </b-card>
    </div>
    <!-- 右半圖表區 -->
    <div class="right">
      <div class="r_modal">
        <!-- 地圖modal-->
        <Map v-if="isMap" :jobType="jobs" :range="range" :mrtjson="mrtjson" :market="market" :morto="morto" :park="park" :gym="gym" @return-mrt="updatemrtdata" @return-market="updatemarketdata" @return-morto="updatemortodata"/>
        <!-- 樹枝modal-->
        <!-- <Branch v-if="!isMap" :jobType="jobs" :range="range"/> -->
      </div>
    </div>
  </div>
</template>

<script>
// 左上圖例
import Icon from './components/Icon.vue'
// 左下評分
// import Score from './components/Score.vue'
// 左下總覽
// import Overview from './components/Overview.vue'
// 右方地圖
import Map from './components/Map.vue'
// 右方樹枝
// import Branch from './components/Branch.vue'
import mrtjson from './高捷.json';
import market from './超市.json';
import morto from './機車行.json';
import park from './公園.json';
import gym from './健身房.json';

export default {
  components:{Map, Icon},
  data(){
    return{
      // 左上行業select
      jobs_selected: 'a',
      jobs:[
        {value:'a', text:'幼兒園'},
        {value:'b', text:'機車行'},
        {value:'c', text:'健身房'}
      ],
      // 左上距離調整
      range: 300,
      // 判斷右方模式
      isMap: true,
      // 應該要有一個儲存選定地點的array? 加權modal會計算並回傳加權分數(假設icon有encode分數高低)
      score: 50,
      mrtjson: mrtjson, //全部mrt資料
      market: market,  //全部超市資料
      morto: morto,
      park: park,
      gym: gym,
      returnmrt: [],  //選取範圍內的Mrt資料
      returnmarket: [], //選取範圍內的Market資料
      returnmorto: [] //選取範圍內的機車行資料
    }
  },
  methods:{
    //接收Map.vue中範圍內捷運站數量並更新至App.vue
    //!!!因為傳object是用call by reference所以不要動到returnmrt和returnmarket!!!
    //避免發生問題可以用deep copy, 不過我還沒弄(這樣也許會有更新不同步的問題?)
    updatemrtdata(element){
      this.returnmrt = element;
    },
    updatemarketdata(element){
      this.returnmarket = element;
    },
    updatemortodata(element){
      this.returnmorto = element;
    }
  }
}
</script>

<style>
#app {
  height: 100%;
  width: 100%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
}
.left{
  height: 100%;
}
.left_top{
  height: 53%;
  width: 380px;
}
.setting{
  display: flex;
  text-align: center;
}
.job{
  width: 90px;
}
.label_lt{
  padding: 10px 5px 0px 10px;
  padding-right: 5px;
}
.card-body{
  padding-top: 8px;
  padding-left: 0px;
}
.distance{
  padding: 8px 5px 0px 15px;
}
.left_down{
  height: 47%;
}
.right{
  height: 100%;
  width: 100%;
  text-align: left;
}
.r_modal{
  height: 100%;
  width: 100%;
}
.r_button{
  /* display: flex; */
  position: absolute; 
  z-index: 100;
  right: 0;
  top: 5%;
  text-align: center;
  margin-right: 20px;
}
.tableline{
  position: relative;
  margin: 0 auto;
  height: 1px;
  background-color: black;
}
.flex{
  display:flex;
  align-items:left;
  margin-bottom: 10px;
}
.custom-range{
  width: 40%;
  padding-top: 18px;
}
.dis_range{
  width: 160px;
}
</style>
