<template>
    <div class="container">
        <!--<p class="title">地點資訊</p>-->
        <!--<div class="tableline">-->
        <p class="lines">預估需求：</p>
        <p></p>
        <p class="lines">租金：</p>
        <p></p>
        <p class="lines">地址：</p>
        <p></p>
        <p class="lines">附近競爭者數：</p>
        <p></p>
        <p class="lines">附近市場數：</p>
        <p></p>
        <p class="lines">附近捷運站數：</p>
        <p></p>
        <p class="lines">區域平均租金：</p>
        <p></p>
        <!--</div>-->
    </div>
</template>

<script>
export default {
    props: ["jobType", "distance"],
    methods: {},
};
</script>

<style scoped>
    .container {
        height: 275px;
        overflow: auto;
    }
    .lines {
        text-align: left;
        font-size: 16px;
    }
    .title {
        font-size: 18px;
        font-weight: bold;
        background-color: #ecffff;
    }
    ::-webkit-scrollbar {
        /*隱藏滾動條*/
        display: none;
    }
</style>
