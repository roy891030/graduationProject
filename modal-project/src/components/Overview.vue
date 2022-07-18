<template>
    <div style="height:275px; overflow:auto">
        <p>地點資訊</p>
        <!--<div class="tableline">-->
          <p style="text-align:left">預估需求：</p>
          <p></p>
          <p style="text-align:left">租金：</p>
          <p></p>
          <p style="text-align:left">地址：</p>
          <p></p>
          <p style="text-align:left">附近競爭者數：</p>
          <p></p>
          <p style="text-align:left">附近市場數：</p>
          <p></p>
          <p style="text-align:left">附近捷運站數：</p>
          <p></p>
          <p style="text-align:left">區域平均租金：</p>
          <p></p>
        <!--</div>-->
</template>

<script>
export default {
    props:['jobType', 'distance'],
    methods:{
    }
}
</script>

<style scoped>
.le{
  text-align:left;
}
</style>