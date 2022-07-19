<template>
        <span style="text-align:left; font-weight:bold; float:left">加權調整</span>
        <span style="text-align:left; font-weight:bold; float:right">評分</span><br><br>
          
        <div style="height:200px; overflow:auto">
          <div v-if="jobs_selected === 'a'"><!--切換行業-->
            <div style="width:300px; text-align:center;"><!--幼兒園-->
              <div style="width:auto; *width:100px; margin:0 auto; display:inline-block;">
                  <span style="width:auto; display:block; text-align:center;">公園
                    <input type="checkbox" style="width:20px; height:20px; float:left">
                  </span>
                  <label for="customRange1" class="form-label">{{scorepark}}%</label><!--可任意調分-->
                  <input type="range" class="form-range" id="customRange1" v-model="scorepark"><br><br>
                  <span style="width:auto; display:block; text-align:center;">捷運站
                    <input type="checkbox" style="width:20px; height:20px; float:left">
                  </span>
                  <label for="customRange1" class="form-label">{{scoremrtone}}%</label>
                  <input type="range" class="form-range" id="customRange1" v-model="scoremrtone"><br><br>
                  <span style="width:auto; display:block; text-align:center;">租金
                    <input type="checkbox" style="width:20px; height:20px; float:left">
                  </span>
                  <label for="customRange1" class="form-label">{{scoremoneyone}}%</label>
                  <input type="range" class="form-range" id="customRange1" v-model="scoremoneyone"><br><br>
              </div>
            </div>
          </div>
          <div v-else-if="jobs_selected === 'b'">
            <div style="width:300px; text-align:center;"><!--機車行-->
              <div style="width:auto; *width:100px; margin:0 auto; display:inline-block;">
                  <span style="width:auto; display:block; text-align:center;">市場
                    <input type="checkbox" style="width:20px; height:20px; float:left">
                  </span>
                  <label for="customRange1" class="form-label">{{scoremarket}}%</label>
                  <input type="range" class="form-range" id="customRange1" v-model="scoremarket">
                  <div style="width:300px; text-align:center;"><!--市場細項-->
                    <div style="width:auto; *width:100px; margin:0 auto; display:inline-block;">
                        <span style="width:auto; display:block; text-align:center;">小北
                          <input type="checkbox" style="width:20px; height:20px; float:left">
                        </span>
                        <span style="width:auto; display:block; text-align:center;">全聯
                          <input type="checkbox" style="width:20px; height:20px; float:left">
                        </span>
                        <span style="width:auto; display:block; text-align:center;">美廉社
                          <input type="checkbox" style="width:20px; height:20px; float:left">
                        </span><br>
                    </div>
                  </div>
                  <span style="width:auto; display:block; text-align:center;">捷運站
                    <input type="checkbox" style="width:20px; height:20px; float:left">
                  </span>
                  <label for="customRange1" class="form-label">{{scoremrttwo}}%</label>
                  <input type="range" class="form-range" id="customRange1" v-model="scoremrttwo"><br><br>
                  <span style="width:auto; display:block; text-align:center;">租金
                    <input type="checkbox" style="width:20px; height:20px; float:left">
                  </span>
                  <label for="customRange1" class="form-label">{{scoremoneytwo}}%</label>
                  <input type="range" class="form-range" id="customRange1" v-model="scoremoneytwo"><br><br>
              </div>
            </div>
          </div>
          <div v-else>
            <div style="width:300px; text-align:center;"><!--健身房-->
              <div style="width:auto; *width:100px; margin:0 auto; display:inline-block;">
                  <span style="width:auto; display:block; text-align:center;">百貨公司
                    <input type="checkbox" style="width:20px; height:20px; float:left">
                  </span>
                  <label for="customRange1" class="form-label">{{scorede}}%</label>
                  <input type="range" class="form-range" id="customRange1" v-model="scorede"><br><br>
                  <!--<div style="width:300px; text-align:center;">
                    <div style="width:auto; *width:100px; margin:0 auto; display:inline-block;">
                      <span style="width:auto; display:block; text-align:center;">大遠百</span>
                      <span style="width:auto; display:block; text-align:center;">新光三越</span>
                      <span style="width:auto; display:block; text-align:center;">SOGO</span>
                     </div>
                  </div>-->
                  <span style="width:auto; display:block; text-align:center;">Ubike
                    <input type="checkbox" style="width:20px; height:20px; float:left">
                  </span>
                  <label for="customRange1" class="form-label">{{scorebike}}%</label>
                  <input type="range" class="form-range" id="customRange1" v-model="scorebike"><br><br>
                  <span style="width:auto; display:block; text-align:center;">捷運站
                    <input type="checkbox" style="width:20px; height:20px; float:left">
                  </span>
                  <label for="customRange1" class="form-label">{{scoremrtthree}}%</label>
                  <input type="range" class="form-range" id="customRange1" v-model="scoremrtthree"><br><br>
                  <span style="width:auto; display:block; text-align:center;">租金
                    <input type="checkbox" style="width:20px; height:20px; float:left">
                  </span>
                  <label for="customRange1" class="form-label">{{scoremoneythree}}%</label>
                  <input type="range" class="form-range" id="customRange1" v-model="scoremoneythree"><br><br>
              </div>
            </div>
          </div>
        </div>
</template>

<script>
export default {
    props:['jobType', 'distance'],
    methods:{
    }
}
</script>

<style scoped>
[type="checkbox"] {
  display: grid;
  place-content: center;
}
</style>