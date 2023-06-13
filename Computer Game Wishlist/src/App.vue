<script>
import Head from './components/Head.vue';
import Body from './components/Body.vue';

export default{
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
      tab: 0
    }
  }
}

</script>

<template>
  <div>
    <h1>Computer Games Wunschliste</h1>
    <Head @filterWishList="setTab"></Head>
    <Body :selectedTab="tab"></Body>
  </div>
</template>

<style scoped>
  *{
    font-family: Arial;
    background-color: steelblue;
  }
  h1{
    text-align: center;
    
  }
</style>
