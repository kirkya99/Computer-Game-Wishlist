<script>
import Head from './components/Head.vue';
import Body from './components/Body.vue';
import axios from 'axios';

export default{
    created(){
        axios.get('https://cors-anywhere.herokuapp.com/https://www.mmobomb.com/api1/games')
            .then(response => {
                console.log(response.data)
                this.gamesArray = response.data
                //this.gamesArray.push(response.data);
            })
            .catch(console.error);
    },
    components:{
        Head, Body
    },
    methods:{
        setTab(value){
            this.tab = value;
        }
    },
    data(){
        return{
            tab: 0,
            gamesArray: [],
        }
    }
}   

</script>

<template>
  <div>
    <h1>Computer Games Wunschliste</h1>
    <Head @filterWishList="setTab"></Head>
    <Body :selectedTab="tab" :games="gamesArray"></Body>
  </div>
</template>

<style scoped>
    *{
        font-family: Arial;
        /*background-color: steelblue;*/
    }
    h1{
        text-align: center;
    }
</style>
