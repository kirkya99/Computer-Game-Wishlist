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
    <table>
        <tr>
            <th class="item">Cover</th>
            <th class="item">Title</th>
            <th class="item">Genre</th>
            <th class="item">Platform</th>
            <th class="item">Publisher</th>
            <th class="item"></th>
        </tr>
        <tr v-for="game in games">
            <td class="item"><img :src="game.thumbnail" alt="No picture available"></td>
            <td class="item">{{ game.title }}</td>
            <td class="item">{{ game.genre }}</td>
            <td class="item">{{ game.platform }}</td>
            <td class="item">{{ game.publisher }}</td>
            <td class="item">
                <button @click="viewGame(game.id)" class="btn">View Game</button>
                <button @click="addToWishlist(game.id)" class="btn">Add to Wishlist</button>
            </td>
        </tr>
    </table> 
</template>

<style>
    t
    .item{
        height: 25px;
        width: 10%;
        text-align: center;
        
    }
    .btn{
        width: 50%;
    }
    table{
        margin-top: 25px;
        width: 90%;
        margin-left: 2.5%;
        margin-right: 2.5%;
    }
    img{
        height: 50px;
    }
</style>