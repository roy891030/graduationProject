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
                <b-form-input id="range-1" v-model="distance" type="range" min="300" max="1500"></b-form-input>  
              </div>
              <div class="mt-2">Value: {{ distance }}</div>
              <!-- 圖例modal, 參數為行業 -->
              <!-- <Icon :jobType="jobs" :distance="distance"/> -->
            </b-tab>
            <b-tab title="圖表">
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
                
              <label for="customRange1" class="form-label">50%</label><!--可任意調分-->
              <input type="range" class="form-range" id="customRange1"><br><br>
              <!-- 加權條整區modal, 參數為行業 -->
              <!-- <Score :jobType="jobs" :distance="distance"/> -->
            </b-tab>
            <b-tab title="總覽">
              <p>地點需求</p>
              <div style="height:300px; overflow:auto">
                <div class="tableline"></div>
                  <p style="text-align:left">預估需求：</p>
                  <p style="text-align:left">租金：</p>
                  <p style="text-align:left">地址：</p><br><br>
                  <p style="text-align:left">附近競爭者數：</p>
                  <p style="text-align:left">附近市場數：</p>
                  <p style="text-align:left">附近捷運站數：</p>
                  <p style="text-align:left">區域平均租金：</p>
              </div>
              <!-- 參數...好像...很多... -->
              <!-- <Overview :jobType="jobs" :distance="distance"/> -->
            </b-tab>
          </b-tabs>
        </b-card>
    </div>    
    <!-- 右半圖表區 -->
    <div class="right">
      <div class="r_modal">
        <!-- 地圖modal-->
        <Map v-if="isMap" :jobType="jobs" :distance="distance" />
        <!-- 樹枝modal-->
        <!-- <Branch v-if="!isMap" :jobType="jobs" :distance="distance"/> -->
      </div>
    </div>
  </div>  
</template>

<script>
// 左上圖例
// import Icon from './components/Icon.vue'
// 左下評分
// import Score from './components/Score.vue'
// 左下總覽
// import Overview from './components/Overview.vue'
// 右方地圖
import Map from './components/Map.vue'
// 右方樹枝
// import Branch from './components/Branch.vue'

export default {
  components:{Map},
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
      distance: 300,
      // 判斷右方模式
      isMap: true
      // 應該要有一個儲存選定地點的array? 加權modal會計算並回傳加權分數(假設icon有encode分數高低)
    }
  }
  // methods: {
  // 切換右側模式
  //   toggleModal(){
  //     this.isMap = !this.isMap
  //   }
  // }
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
  width: 450px;
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
</style>
