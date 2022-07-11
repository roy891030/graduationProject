<template>
<div style="height:100%">
    <l-map style="height: 100%" :zoom="zoom" :center="center" @click="addSelect" id="lmap">
        <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
        <l-circle v-for="marker in newCircleDetails" :key="marker.id"
          :lat-lng="marker.location"
          :radius="distance"
          :color="marker.color"
          :fillOpacity="marker.fillOpacity"
        />
        <!-- 創建標記點 -->
        <l-marker  v-for="item in mrtData" :lat-lng="[item.Latitude, item.Longitude]" >
        <!-- 標記點樣式 -->
          <l-icon
            :icon-url="icon.iconType.mrt"
            :icon-size="icon.iconSize.tri" 
          />
          <l-popup>
            {{ "捷運"+item.StationNameZh+"站" }}
          </l-popup>
        </l-marker>
        <!-- 創建標記點 -->
        <l-marker  v-for="item in marketData" :lat-lng="[item.Latitude, item.Longitude]" >
        <!-- 標記點樣式 -->
          <l-icon 
            v-if="item.品牌 === '小北'"
            :icon-url="icon.iconType.小北"
            :icon-size="icon.iconSize.squ" 
          />
          <l-icon 
            v-if="item.品牌 === '全聯'"
            :icon-url="icon.iconType.全聯"
            :icon-size="icon.iconSize.squ" 
          />
          <l-icon 
            v-if="item.品牌 === '美廉社'"
            :icon-url="icon.iconType.美廉"
            :icon-size="icon.iconSize.squ" 
          />
          <l-popup>
            {{ item.品牌+item.門市 }}
          </l-popup>
        </l-marker>
        <l-control  class="r_button">
            <b-button variant="primary" @click="isPush">新增地點</b-button><br><br>
            <!-- <b-button variant="secondary" >刪除地點</b-button><br><br> -->
            <b-dropdown right text="刪除地點" V-if>
              <b-dropdown-item v-for="marker in newCircleDetails" @click="deleteSelect(marker.id)">{{marker.location}}</b-dropdown-item>
            </b-dropdown><br><br>
            <b-button  variant="info">切換模式</b-button>
        </l-control>
    </l-map>
    </div>
</template>

<script>
import {LMap, LTileLayer, LControl, LCircle, LCircleMarker, LMarker, LIcon, LPopup} from 'vue2-leaflet';
import "leaflet/dist/leaflet.css";

import mrtjson from '../高捷.json';
import market from '../超市.json';

export default {
  props:['distance'],
  components: {
    LMap,
    LTileLayer,
    LControl,
    LCircle,
    LCircleMarker,
    LMarker,
    LIcon,
    LPopup
  },
  data () {
    return {
      url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      attribution:
        '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      zoom: 10.8,
      center: [ 22.62, 120.33],
      push: false,
      newCircleDetails:[],
      icon: {
        iconType: {
          mrt: "http://localhost/mrt.png",
          小北: "http://localhost/小北.jpg",
          全聯: "http://localhost/全聯.png",
          美廉: "http://localhost/美廉.png"
        },
        iconSize: {
          tri: [41, 25],
          squ: [25, 20]
        },
        iconAnchor: [12, 41],
      },
      mrtData: mrtjson,
      marketData: market
    };
  },
  methods:{
      //似乎該reuse喔
      addSelect(event) {
        if(this.push){
          this.newCircleDetails.push({
            id: this.newCircleDetails.length,
            location: [event.latlng.lat, event.latlng.lng],
            color:'red',
            fillOpacity: 0.3
          })
        }
        this.push = false
      },
      isPush(){
          this.push = true
      },
      deleteSelect(key){
          this.newCircleDetails.splice(key, 1);
          // console.log(key)
          var temp = []
          this.newCircleDetails.forEach((element)=>{
            temp.push(element)
            temp[temp.length-1].id = temp.length-1
          })
          this.newCircleDetails = temp
      }
  }
}
</script>

<style>
l-tile-layer{
    z-index: 0;
}
.r_button{
  /* display: flex; */
  position: absolute; 
  z-index: 100;
  right: 0;
  top: 5%;
  text-align: center;
  margin-right: 20px;
  width: 100px;
}
</style>