<script>
import Head from './components/Head.vue';
import Body from './components/Body.vue';
import axios from 'axios';

export default{
    created(){
    /*
     * Code Snippet from https://github.com/Rob--W/cors-anywhere/#documentation:
     */
    (function() {
        var cors_api_host = 'cors-anywhere.herokuapp.com';
        var cors_api_url = 'https://' + cors_api_host + '/';
        var slice = [].slice;
        var origin = window.location.protocol + '//' + window.location.host;
        var open = XMLHttpRequest.prototype.open;
        XMLHttpRequest.prototype.open = function() {
            var args = slice.call(arguments);
            var targetOrigin = /^https?:\/\/([^\/]+)/i.exec(args[1]);
            if (targetOrigin && targetOrigin[0].toLowerCase() !== origin &&
                targetOrigin[1] !== cors_api_host) {
                args[1] = cors_api_url + args[1];
            }
            return open.apply(this, args);
        };
    })();
    /*
     * End Code Snippet
     */
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
    <h1>Computer Games Wishlist</h1>
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
