<template>
<div style="height:100%"> 
    <l-map style="height: 100%" :zoom="zoom" :center="center" @click="addSelect" id="lmap" :max-bounds="maxBounds" ref="myMap">
        <!--底圖圖層-->
        <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
        <!-- 使用者選取範圍 -->
        <l-circle v-for="marker in newCircleDetails" :key="marker.id" :lat-lng="marker.location"
          :radius="range" :color="marker.color" :fillOpacity="marker.fillOpacity"/>
        <!--捷運站圖層-->
        <l-layer-group ref="mrts">
          <!-- 創建標記點 !!!!!地圖上捷運站的位置跟我們顯示的有誤差!!!!--> 
          <l-marker  v-for="item in mrt_filter()" :lat-lng="item.location">
            <!-- 標記點樣式 -->
            <l-icon :icon-url="icon.iconType.mrt" :icon-size="icon.iconSize.zoom14.tri" />
            <!-- 點擊跳出地點資訊 -->
            <l-popup>{{ "捷運"+item.zh_name+"站" }}</l-popup>
          </l-marker>
        </l-layer-group>
        <!--市場圖層-->
        <l-layer-group ref="markets">
          <!-- 創建標記點 -->
          <l-marker  v-for="item in market_filter()" :lat-lng="item.location" >
          <!-- 標記點樣式 -->
            <l-icon v-if="item.brand === '小北'" :icon-url="icon.iconType.小北" :icon-size="icon.iconSize.zoom14.squ"/>
            <l-icon v-if="item.brand === '全聯'" :icon-url="icon.iconType.全聯" :icon-size="icon.iconSize.zoom14.squ"/>
            <l-icon v-if="item.brand === '美廉社'" :icon-url="icon.iconType.美廉" :icon-size="icon.iconSize.zoom14.squ"/>
            <l-popup>{{ item.brand + item.name }}</l-popup>
          </l-marker>
        </l-layer-group>
        <l-control  class="r_button">
            <b-button variant="primary" @click="isPush">新增地點</b-button><br><br>
            <b-dropdown right text="刪除地點" V-if>
              <b-dropdown-item v-for="marker in newCircleDetails" @click="deleteSelect(marker.id, marker.location)" :key="marker.id">{{marker.location}}</b-dropdown-item>
            </b-dropdown><br><br>
            <b-button  variant="info">切換模式</b-button>
        </l-control>
    </l-map>
</div>
</template>

<script>
import { latLngBounds, latLng } from "leaflet";
import {LMap, LTileLayer, LControl, LCircle, LCircleMarker, LMarker, LIcon, LPopup, LLayerGroup} from 'vue2-leaflet';
import "leaflet/dist/leaflet.css";
import mrtjson from '../高捷.json';
import market from '../超市.json';

export default {
  props:['range'],
  components: {LMap, LTileLayer, LControl, LCircle, LCircleMarker, LMarker, LIcon, LPopup, LLayerGroup},
  data () {
    return {
      url: 'https://tiles.stadiamaps.com/tiles/alidade_smooth/{z}/{x}/{y}{r}.png',
      attribution:
        '&&copy; <a href="https://stadiamaps.com/">Stadia Maps</a>, &copy; <a href="https://openmaptiles.org/">OpenMapTiles</a> &copy; <a href="http://openstreetmap.org">OpenStreetMap</a> contributors',
      zoom: 14,//初始縮放比例
      center: [ 22.62, 120.33],// 地圖中心點
      push: false,//判斷使用者是否要新增選取地點
      newCircleDetails:[],//紀錄使用者選去地點與範圍資料
      maxBounds: latLngBounds([// 設定地圖邊界
        [22.229573497276068, 119.66995239257814],
        [22.901501217049034, 120.8280395507814]
      ]),
      icon: {
        iconType: {
          mrt: "http://localhost/mrt.png",
          小北: "http://localhost/小北.jpg",
          全聯: "http://localhost/全聯.png",
          美廉: "http://localhost/美廉.png"
        },
        iconSize: {
          zoom14: {
            tri: [41, 25],
            squ: [25, 20]
          },
          zoom18: {
            tri: [0, 0],
            squ: [0, 0]
          }
        },
      },
      to_load_mrt: true,//控制建立mrtData的參數，避免mrtData一直重建(circle_times會被洗掉)
      mrtData: [],// 紀錄在圓圈範圍內要顯示的mrt
      to_load_market: true,//控制建立 marketData的參數，避免 marketData一直重建(circle_times會被洗掉)
      marketData:[]// 紀錄在圓圈範圍內要顯示的超市
    };
  },
  mounted () {
    //縮放監聽事件
    this.$refs.myMap.mapObject.addEventListener('zoomend', this.handleScroll, true);
  },
  methods:{
      addSelect(event) {// 新增使用者選取地點 與 週邊權重地點
        if(this.push){
          this.newCircleDetails.push({// 新增圓圈到陣列裡
            id: this.newCircleDetails.length,
            location: [event.latlng.lat, event.latlng.lng],
            color:'red',
            fillOpacity: 0.3
          })
          for(let i = 0; i < mrtjson.length; i++){
            if(this.to_load_mrt){ // 把捷運json檔資料另存成陣列格式
              var temp_latlng =  L.latLng(mrtjson[i].Latitude, mrtjson[i].Longitude); //把車站的經緯度合併成leaflet使用的格式
              this.mrtData.push({// 把捷運json檔資料另存成陣列格式
                id: this.mrtData.length, // 就...給個編號
                location: temp_latlng, // 座標
                zh_name: mrtjson[i].StationNameZh,// 車站中文名
                en_name: mrtjson[i].StationNameEn,// 車站英文名
                addr: mrtjson[i].StationAddress, // 車站地址
                circle_times: 0 //紀錄該車站被框到的次數，用來控制icon是否顯示
              })           
              if(i == (mrtjson.length-1)){ // 避免重複讀取資料到陣列
                this.to_load_mrt = !this.to_load_mrt;
              }
            }
            if(this.mrtData[i].location.distanceTo(this.newCircleDetails[this.newCircleDetails.length -1].location) < this.range){ // 判斷那些站被新增的圓圈框到
              this.mrtData[i].circle_times = this.mrtData[i].circle_times + 1;
            }
          }
          // console.log(this.to_load_mrt);
          for(let i = 0; i < market.length; i++){
            if(this.to_load_market){ // 把超市json檔資料另存成陣列格式
              var temp_latlng =  L.latLng(market[i].Latitude, market[i].Longitude); //把超市的經緯度合併成leaflet使用的格式
              this.marketData.push({// 把超市json檔資料另存成陣列格式
                id: this.marketData.length, // 就...給個編號
                location: temp_latlng, // 座標
                brand: market[i].品牌,// 超市品牌
                name: market[i].門市,
                addr: market[i].地址, // 超市地址
                circle_times: 0 //紀錄該超市被框到的次數，用來控制icon是否顯示
              })  
              if(i == (market.length-1)){ // 避免重複讀取資料到陣列
                this.to_load_market = !this.to_load_market;
              }
            }
            if(this.marketData[i].location.distanceTo(this.newCircleDetails[this.newCircleDetails.length -1].location) < this.range){ // 判斷那些站被新增的圓圈框到
              this.marketData[i].circle_times = this.marketData[i].circle_times + 1;
            }
          }
          this.push = false; 
        }
      },
      isPush(){
          this.push = true
      },
      deleteSelect(key, location){
        // 刪除使用者選取的地點
        this.newCircleDetails.splice(key, 1);
        var temp = []
        this.newCircleDetails.forEach((element)=>{
          temp.push(element)
          temp[temp.length-1].id = temp.length-1
        })
        this.newCircleDetails = temp;
        // 刪除圓圈後變成沒被選到的捷運其選取次數減1
        this.$nextTick(()=>{
          for(let i = 0; i < this.mrtData.length; i++){
            if(this.mrtData[i].location.distanceTo(location) < this.range){
              this.mrtData[i].circle_times = this.mrtData[i].circle_times - 1;
            }
          }
        })
        // 刪除圓圈後變成沒被選到的超市其選取次數減1
        this.$nextTick(()=>{
          for(let i = 0; i < this.marketData.length; i++){
            if(this.marketData[i].location.distanceTo(location) < this.range){
              this.marketData[i].circle_times = this.marketData[i].circle_times - 1;
              // console.log(this.mrtData[i].circle_times);
            }
          }
        })
      },
      mrt_filter(){ //過濾要呈現icon捷運，只呈現 circle_times 大於0的捷運站的 icon
        var temp = [];
        this.mrtData.forEach((element) =>{
          if(element.circle_times > 0){
            temp.push(element); 
          }
        })
        return temp;
      },
      market_filter(){ //過濾要呈現icon市場，只呈現 circle_times 大於0的市場的 icon
        var temp = [];
        this.marketData.forEach((element) =>{
          if(element.circle_times > 0){
            temp.push(element); 
          }
          // console.log(element.circle_times)
        })
        return temp;
      },
      //地圖縮放之後決定該顯示的圖層
      handleScroll(){
        //獲取當前縮放大小
        var temp = this.$refs.myMap.mapObject.getZoom();
        //確認當前是否有圖層:有才能刪除圖層
        if(this.$refs.myMap.mapObject.hasLayer(this.$refs.markets.mapObject) && this.$refs.myMap.mapObject.hasLayer(this.$refs.mrts.mapObject)){
          if(temp <= 14){
            //移除圖層
            this.$refs.myMap.mapObject.removeLayer(this.$refs.markets.mapObject);
            this.$refs.myMap.mapObject.removeLayer(this.$refs.mrts.mapObject);
          }
        }
        else{
          if(temp >= 14){
            //加入圖層
            this.$refs.myMap.mapObject.addLayer(this.$refs.markets.mapObject, false);
            this.$refs.myMap.mapObject.addLayer(this.$refs.mrts.mapObject, false);
          }
        }
      }
  }
}
</script>

<style>
l-tile-layer{
    z-index: 0;
}
.r_button{
  position: absolute; 
  z-index: 100;
  right: 0;
  top: 5%;
  text-align: center;
  margin-right: 20px;
  width: 100px;
}
</style>