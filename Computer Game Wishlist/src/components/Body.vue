<script>
import List from './List.vue';

export default{
    props: ['selectedTab', 'games'],
    components:{
        List
    },
    data(){
        return{
            selectedGameIndex: 0,
            wishlist: [],
            selectedView: 0 //0 = List, 1 = Single Game View
        }
    },
    methods:{
        showGame(gameId){
            this.findGame(gameId);

        },
        findGame(gameId){
            
        }
    }   
}

    
</script>

<template>
    <div v-if="selectedTab==0">
        <List :games="games" @viewGame="showGame(gameId)"></List>
    </div>
    <div v-if="selectedTab==1">
        <h2>Wunschliste</h2>
    </div>
</template>

