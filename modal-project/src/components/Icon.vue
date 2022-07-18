<!-- 小人依據不同的職業拿不同的東西 -->
<!-- icon animation -->
<!-- 租金data如何流到這個vue -->


<template>
    <b-container>
        <b-row align-v="center">

            <div class="text-center" v-show="select==='a'">
                <img src="../svg/vuePerson.svg" alt="" width="80%">
                <img src="../svg/bag.svg" alt="" width="80%">
                <img src="../svg/flag.svg" alt="" width="80%">
            </div>

            <div v-show="select === 'b'">
                <img src="../svg/vuePerson.svg" alt="" width="80%">
                <img src="../svg/bag.svg" alt="" width="80%">
                <img src="../svg/flag.svg" alt="" width="80%">
            </div>

            <div v-show="select === 'c'">
                <img src="../svg/vuePerson.svg" alt="" width="80%">
                <img src="../svg/bag.svg" alt="" width="80%">
                <img src="../svg/flag.svg" alt="" width="80%">
            </div>

        </b-row>
    </b-container>

</template>

<script>

export default {
    props: ['jobType', 'distance','select' ],

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



img{
    position:absolute;
    width:70%;
}
</style>