<script>
export default{
    emits: ['filterWishList'],    
    data() {
    return {
        //hover1: false,
        //hover2: false
    }
  },
  methods:{
    switchToGamesList(){
        this.$emit('filterWishList',0);
    },
    switchToWishlist(){
        this.$emit('filterWishList',1);
    }
  }
}
</script>

<template>
    <div id="header">
        <div class="header_bar">
            <div class="header_item" role="button" id="gameslist" @click="switchToGamesList">
                <h2>Neue Spiele</h2>
            </div>
            <div class="header_item" role="button" id="wishlist" @click="switchToWishlist">
                <h2>Wunschliste</h2>
            </div>
        </div>
    </div>
</template>

<style scoped>
    *{
        font-family: Arial;
    }
    #header{
        width: 100%;
        background-color: lightblue;
    }
    .header_bar{
        display: flex;
        background-color: dodgerblue;
    }
    .header_item{
        width: 50%;
        text-align: center;
    }
    #gameslist:hover{
        background-color: lightblue;
    }
    #wishlist:hover{
        background-color: lightblue;
    }
</style>