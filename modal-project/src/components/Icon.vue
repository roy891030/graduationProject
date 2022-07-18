<!-- icon animation -->
<!-- 租金data如何流到這個vue -->


<template>
    <b-container>
        <b-row align-v="center">

            <div v-show="select==='a'">
                <img class="person" src="../assets/vuePerson.svg" alt="">
                <img class="right" src="../assets/flower.svg" alt="">
                <img class="left" src="../assets/flag.svg" alt="">

            </div>

            <div v-show="select === 'b'">
                <img class="person" src="../assets/vuePerson.svg" alt="" width="80%">
                <img class="right" src="../assets/bag.svg" alt="" width="80%">
                <img class="left" src="../assets/flag.svg" alt="" width="80%">
            </div>

            <div v-show="select === 'c'">
                <img class="person" src="../assets/vuePerson.svg" alt="" width="80%">
                <img class="right" src="../assets/bag.svg" alt="" width="80%">
                <img class="left" src="../assets/flag.svg" alt="" width="80%">
            </div>

        </b-row>
    </b-container>

</template>

<script>
export default {
    props: ['jobType','select' ],

    data(){
        return{
            roy: "cool",
        }

    },
    methods:{
    }

}
</script>

<style scoped>







@keyframes example {
    0% {
    top: 140px;
    }
    50% {
    top: 110px;
    transform: rotate(-10deg)
    }
    100% {
    top: 140px;
    }
}

@keyframes example2 {
    0% {
    top: 170px;
    left: 180px;

    }

    50% {
    top: 100px;
    left: 190px;
    transform: rotate(45deg)

    }

    100% {
    top: 170px;
    left: 180px;
    }
}

svg.liquid{
    position:absolute;

}

.left{
    position: absolute;
    width: 130px;
    height: 130px;
            left: 10px;
    animation-name: example;
    
    animation-duration: 2s;
    animation-iteration-count: 1000000;
}



.person{
    position: absolute;
    top:140px;
    left:100px;
    width:30%;
}


.right{
position: absolute;
    animation-name: example2;
    animation-duration: 2s;
    animation-iteration-count: 1000000;
    width: 80px;
    height: 80px;
}

</style>