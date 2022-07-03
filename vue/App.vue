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
                <b-card-text>行業</b-card-text>
                <b-form-select v-model="selected" :options="options" class="job"></b-form-select>
                <b-card-text class="distance">距離</b-card-text>
                <b-form-select v-model="selected" :options="none" class="job"></b-form-select>
              </div>
            </b-tab>
            <b-tab title="圖表">
              <b-card-text>圖表</b-card-text>
              <!-- <b-card-img bottom src="https://picsum.photos/400/200/?image=26" alt="Image 26"></b-card-img> -->
            </b-tab>
          </b-tabs>
        </b-card>
        <!-- 左下的tab -->
        <b-card no-body class="left_down">
          <b-tabs card>
            <b-tab title="評分" active>
              <b-card-text>評分 modal</b-card-text>
            </b-tab>
            <b-tab title="總覽">
              <b-card-text>總覽</b-card-text>
            </b-tab>
          </b-tabs>
        </b-card>
    </div>    
    <!-- 右半圖表區 -->
    <div class="right">

    </div>
  </div>  
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  data(){
    return{
      selected: 'a',
      options:[
        {value:'a', text:'幼兒園'},
        {value:'b', text:'機車行'},
        {value:'c', text:'健身房'}
      ]
    }
  }
  // components: {

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
.card-text{
  padding: 8px 5px 0px 0px;
  padding-right: 5px;
}
.card-body{
  padding-top: 8px;
}
.distance{
  padding: 8px 5px 0px 15px;
}
.left_down{
  height: 47%;
}
.right{
  height: 100%;
}
</style>
