<script>
import List from './List.vue';

export default{
    props: ['selectedTab', 'games', 'wishlist'],
    components:{
        List
    },
    data(){
        return{
            selectedGameIndex: 0,
            wishlist: []
        }
    }   
}

    
</script>

<template>
    <div v-if="selectedTab==0">
        <List :games="games"></List>
    </div>
    <div v-if="selectedTab==1">
        <h2>Wunschliste</h2>
    </div>
</template>

