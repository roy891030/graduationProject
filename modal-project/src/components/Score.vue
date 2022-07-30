<template>
<div>
    <span class="scoretitle_r">加權調整</span>
    <span class="scoretitle_l">分</span><br>
    <div class="tableline">
      <div class="scroll1"><!--滾動條-->
          <!--幼兒園-->
          <div v-if="jobType === 'a'"><!--切換行業-->
              <div class="jobword">
                  <div>
                      <div type="checkbox" id="Odivpark" class="Odivfirst" @click="show_park()">
                      <div class="flower_p"><img src="../assets/score_pic/flower_score.svg"></div>
                      <p class="word_park">公園</p></div><br>
                      <input type="number" min="0" max="100" step="1" id="number" v-model="park_weight">
                      <input type="range" v-model="park_weight"><br><br><br>
                      <div type="checkbox" id="Odivmrt1" class="Odiv" @click="show_mrt1()">
                      <div class="mrt_p"><img src="../assets/score_pic/mrt_score.svg"></div>
                      <p class="word_mrt">捷運站</p></div><br>
                      <input type="number" min="0" max="100" step="1" id="number" v-model="mrt_weight_kinder">
                      <input type="range" v-model="mrt_weight_kinder"><br><br><br>
                      <div type="checkbox" id="Odivmoney1" class="Odiv" @click="show_rent1()">
                      <p class="word_money">租金</p></div><br>                 
                      <input type="number" min="0" max="100" step="1" id="number" v-model="rent_weight_kinder">
                      <input type="range" v-model="rent_weight_kinder"><br><br><br>
                  </div>
              </div>
          </div>
          <!--機車行-->
          <div v-else-if="jobType === 'b'">
              <div class="jobword">
                  <div>
                      <div type="checkbox" id="Odivmarket" class="Odivfirst" @click="show_market()">
                      <div class="mkt_p"><img src="../assets/score_pic/shop_score.svg"></div>
                      <p class="word_mkt">市場</p></div><br>
                      <input type="number" min="0" max="100" step="1" id="number" v-model="market_weight">
                      <input type="range" v-model="market_weight">
                      <div>
                          <div type="checkbox" id="Odivy" class="Odivy" @click="Y()">
                          <p class="mkt_detail">小北</p></div>
                          <div type="checkbox" id="Odivb" class="Odivb" @click="B()">
                          <p class="mkt_detail">全聯</p></div>
                          <div type="checkbox" id="Odivp" class="Odivp" @click="P()">
                          <p class="mkt_detail">美廉社</p></div>
                      </div><br><br><br>                     
                      <div type="checkbox" id="Odivmrt2" class="Odiv" @click="show_mrt2()">
                          <div class="mrt_p"><img src="../assets/score_pic/mrt_score.svg"></div>
                          <p class="word_mrt">捷運站</p>
                      </div><br>
                      <input type="number" min="0" max="100" step="1" id="number" v-model="mrt_weight_moto">
                      <input type="range" v-model="mrt_weight_moto"><br><br><br>
                      <div type="checkbox" id="Odivmoney2" class="Odiv" @click="show_rent2()">
                          <p class="word_money">租金</p>
                      </div><br>                     
                      <input type="number" min="0" max="100" step="1" id="number" v-model="rent_weight_moto">
                      <input type="range" v-model="rent_weight_moto"><br><br><br>
                  </div>
              </div>
          </div>
          <!--健身房-->
          <div v-else>
              <div class="jobword">
                  <div>
                      <div type="checkbox" id="Odivde" class="Odivfirst" @click="show_department()">
                      <div class="mkt_p"><img src="../assets/score_pic/bag_score.svg"></div>
                      <p class="word_de">百貨公司</p></div><br>                      
                      <input type="number" min="0" max="100" step="1" id="number" v-model="deparment_weight">
                      <input type="range" v-model="deparment_weight"><br><br><br>
                      <div type="checkbox" id="Odivbike" class="Odiv" @click="show_ubike()">
                      <div class="bike_p"><img src="../assets/score_pic/bike_score.svg"></div>  
                      <p class="word_bike">Ubike</p></div><br>                     
                      <input type="number" min="0" max="100" step="1" id="number" v-model="ubike_weight">
                      <input type="range" v-model="ubike_weight"><br><br><br>
                      <div type="checkbox" id="Odivmrt3" class="Odiv" @click="show_mrt3()">
                      <div class="mrt_p"><img src="../assets/score_pic/mrt_score.svg"></div>
                      <p class="word_mrt">捷運站</p></div><br>                        
                      <input type="number" min="0" max="100" step="1" id="number" v-model="mrt_weight_gym">
                      <input type="range" v-model="mrt_weight_gym"><br><br><br>
                      <div type="checkbox" id="Odivmoney3" class="Odiv" @click="show_rent3()">
                      <p class="word_money">租金</p></div><br>
                      <input type="number" min="0" max="100" step="1" id="number" v-model="rent_weight_gym">
                      <input type="range" v-model="rent_weight_gym"><br><br><br>
                  </div>
              </div>
          </div>
      </div>
    </div>
</div>
</template>

<script>
export default {
props:['jobType', 'distance'],
data(){
    return{
        park_weight: 50,
        mrt_weight_kinder:50,
        rent_weight_kinder:50,
        market_weight:50,
        mrt_weight_moto:50,
        rent_weight_moto:50,
        deparment_weight:50,
        ubike_weight:50,
        mrt_weight_gym:50,
        rent_weight_gym:50,
        time_y: false,
        time_b: false,
        time_p: false,
        time_park: false,
        time_mrt_kinder: false,
        time_rent_kinder: false,
        time_market: false,
        time_mrt_moto: false,
        time_rent_moto: false,
        time_department: false,
        time_ubike: false,
        time_mrt_gym: false,
        time_rent_gym: false 
    }
},
methods:{
    Y(){//小北勾選
      if(this.time_y == false){
        document.getElementById("Odivy").style.background="#FFFF00";
        this.time_y = !this.time_y
      }else{
        document.getElementById("Odivy").style.background="white";
        this.time_y = !this.time_y
      }
    },
    B(){//全聯勾選
      if(this.time_b == flase){
        document.getElementById("Odivb").style.background="blue";
        this.time_b = !this.time_b
      }else{
        document.getElementById("Odivb").style.background="white";
        this.time_b = !this.time_b
      }
    },
    P(){//美廉社勾選
      if(this.time_p == false){
        document.getElementById("Odivp").style.background="purple";
        this.time_p = !this.time_p
      }else{
        document.getElementById("Odivp").style.background="white";
        this.time_p = !this.time_p
      }
    },
    show_park(){//幼_公園勾選
      if(this.time_park == false){
        document.getElementById("Odivpark").style.background="black";
        this.time_park = !this.time_park
      }else{
        document.getElementById("Odivpark").style.background="white";
        this.time_park = !this.time_park
      }
    },
    show_mrt1(){//幼_捷運勾選
      if(this.time_mrt_kinder == false){
        document.getElementById("Odivmrt1").style.background="black";
        this.time_mrt_kinder = !this.time_mrt_kinder
      }else{
        document.getElementById("Odivmrt1").style.background="white";
        this.time_mrt_kinder = !this.time_mrt_kinder
      }
    },
    show_rent1(){//幼_租金勾選
      if(this.time_rent_kinder == false){
        document.getElementById("Odivmoney1").style.background="black";
        this.time_rent_kinder = !this.time_rent_kinder
      }else{
        document.getElementById("Odivmoney1").style.background="white";
        this.time_rent_kinder = !this.time_rent_kinder
      }
    },
    show_market(){//機_市場勾選
      if(this.time_market == false){
        document.getElementById("Odivmarket").style.background="black";
        this.time_market = !this.time_market
        Y();
        B();
        P();
      }else{
        document.getElementById("Odivmarket").style.background="white";
        this.time_market = !this.time_market
      }
    },
    show_mrt2(){//機_捷運勾選
      if(this.time_mrt_moto == false){
        document.getElementById("Odivmrt2").style.background="black";
        this.time_mrt_moto = !this.time_mrt_moto
      }else{
        document.getElementById("Odivmrt2").style.background="white";
        this.time_mrt_moto = !this.time_mrt_moto
      }
    },
    show_rent2(){//機_租金勾選
      if(this.time_rent_moto == false){
        document.getElementById("Odivmoney2").style.background="black";
        this.time_rent_moto = !this.time_rent_moto
      }else{
        document.getElementById("Odivmoney2").style.background="white";
        this.time_rent_moto = !this.time_rent_moto
      }
    },
    show_department(){//健_百貨公司勾選
      if(this.time_department == false){
        document.getElementById("Odivde").style.background="black";
        this.time_department = !this.time_department
      }else{
        document.getElementById("Odivde").style.background="white";
        this.time_department = !this.time_department
      }
    },
    show_ubike(){//健_腳踏車勾選
      if(this.time_ubike == false){
        document.getElementById("Odivbike").style.background="black";
        this.time_ubike = !this.time_ubike
      }else{
        document.getElementById("Odivbike").style.background="white";
        this.time_ubike = !this.time_ubike
      }
    },
    show_mrt3(){//健_捷運勾選
      if(this.time_mrt_gym == false){
        document.getElementById("Odivmrt3").style.background="black";
        this.time_mrt_gym = !this.time_mrt_gym
      }else{
        document.getElementById("Odivmrt3").style.background="white";
        this.time_mrt_gym = !this.time_mrt_gym
      }
    },
    show_rent3(){//健_租金勾選
      if(this.time_rent_gym == false){
        document.getElementById("Odivmoney3").style.background="black";
        this.time_rent_gym = !this.time_rent_gym
      }else{
        document.getElementById("Odivmoney3").style.background="white";
        this.time_rent_gym = !this.time_rent_gym
      }
    }
}
}
</script>

<style>
.scoretitle_r{
  text-align:left;
  font-weight:bold;
  margin-right: 100px;
}
.scoretitle_l{
  text-align:left;
  font-weight:bold;
  margin-left: 100px;
}
.tableline{
  width: 100%;
  height: 1px;
  border-top: solid black 1px;
}
.scroll1{
  height:200px;
  overflow:auto; 
}
.jobword{
  width:300px;
  text-align:center;
}
.word_park{
  font-size: 18px;
  margin-top: -15px; 
  margin-right: -150px;
}
.word_mrt{
  font-size: 18px; 
  margin-top: -40px; 
  margin-right: -200px;
}
.word_money{
  font-size: 18px;
  margin-top: -5px; 
  margin-right: -80px;
}
.word_mkt{
  font-size: 18px; 
  margin-top: -15px; 
  margin-right: -150px;
}
.word_de{
  font-size: 18px; 
  margin-top: -15px; 
  margin-right: -170px;
}
.word_bike{
  font-size: 18px; 
  margin-top: -40px; 
  margin-right: -190px;
}
.mkt_detail{
  font-size: 16px; 
  margin-top: -5px; 
  margin-right: -100px;
}
.flower_p{
  width:25px; 
  height: 25px; 
  margin-top: -15px; 
  margin-left: 30px;
}
.mrt_p{
  width:45px; 
  height: 45px; 
  margin-top: -10px;
  margin-left: 30px;
}
.mkt_p{
  width:25px; 
  height: 25px; 
  margin-top: -15px; 
  margin-left: 30px;
}
.de_p{
  width: 30px;
  height: 30px;
  margin-left:20px;
  margin-top: -5px;
}
.bike_p{
  width:45px;
  height: 45px;
  margin-top: -5px; 
  margin-left: 30px;
}
#number{
  width: 3em;
}
.Odivfirst{
  width: 20px;
  height:20px;
  margin-top: 20px;
  border:1px black solid;
  cursor: pointer;
}
.Odiv{
  width: 20px;
  height:20px;
  margin-top: -20px;
  border:1px black solid;
  cursor: pointer;
}
.Odivy{
  width: 20px; 
  height:20px; 
  margin-top: 10px; 
  margin-left: 80px; 
  border:3px #FFFF00 solid;
  cursor: pointer;
}
.Odivb{
  width: 20px; 
  height:20px; 
  margin-top: 10px; 
  margin-left: 80px; 
  border:3px blue solid;
  cursor: pointer;
}
.Odivp{
  width: 20px; 
  height:20px; 
  margin-top: 10px; 
  margin-left: 80px; 
  border:3px purple solid;
  cursor: pointer;
}
::-webkit-scrollbar{/*隱藏滾動條*/
  display: none;
}
</style>