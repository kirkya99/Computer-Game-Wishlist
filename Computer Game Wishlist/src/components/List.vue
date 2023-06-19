<script>
export default{
    props: ['games'],
    emits: ['viewGame', 'addToWishlist'],
    methods:{
        viewGame(gameId){
            this.$emit('viewGame',gameId);
        },
        addToWishlist(gameId){
            this.$emit('addToWishlist', gameId);
        }
    }
}
</script>

<template>
    <h2>Alle Spiele</h2>
        <template>
            <div>
                Titel
            </div>
        </template>
        
        <template v-for="game in games">
            <div class="item">
               {{ game.title }} {{ game.genre }} {{ game.platform }} {{ game.publisher }} 
               <button @click="viewGame(game.id)">View Game</button>
               <button @click="addToWishlist(game.id)">Add to Wishlist</button>
            </div>
        </template>
</template>

<style>
    .item{
        margin: 20px;
        height: 50px;
        border: black;
        border-style: solid;
        border-width: 2px;
        text-align: left;
    }
</style>