<script>
import FilterBar from './FilterBar.vue';

export default {
    props: ['games'],
    emits: ['viewGame', 'addToWishlist'],
    methods: {
        viewGame(gameId) {
            this.$emit('viewGame', gameId);
        },
        addToWishlist(gameId) {
            this.$emit('addToWishlist', gameId);
        }
    },
    components: {
        FilterBar
    }
}
</script>

<template>
    <FilterBar></FilterBar>
    <table>
        <tr>
            <th class="cover">Cover</th>
            <th class="item">Title</th>
            <th class="item">Genre</th>
            <th class="item">Platform</th>
            <th class="item">Publisher</th>
            <th class="item"></th>
        </tr>
    </table>
    <div id="scroll">
        <table>
            <tr v-for="game in games">
                <td class="cover"><img :src="game.thumbnail" alt="No picture available"></td>
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
    </div>
</template>

<style scoped>
th {
    font-size: 25px;
}

td {
    font-size: 18px;
}

table,
th,
td {
    border: 1px solid;
    border-color: steelblue;
    border-collapse: collapse;
}

th,
td {
    border-left: none;
    border-right: none;
}

.item {
    height: 75px;
    width: 10%;
    text-align: left;
}

.btn {
    width: 50%;
    height: 75px;
    font-size: 18px;
}

table {
    width: 100%;
}

img {
    height: 75px;
}

.cover {
    width: 5%;
    height: 75px;
    text-align: left;
}

#scroll {
    overflow-y: scroll;
    height: 990px;
    width: 100%;
}
</style>