<script>
import FilterBar from './FilterBar.vue';

export default {
    props: ['wishlist'],
    components: {
        FilterBar
    }

}

</script>

<template>
    <FilterBar @filterGames="receiveFilter"></FilterBar>
    <div id="tableBackground">
        <div id="tableHeader">
            <table>
                <tr id="headerRow">
                    <th class="cover" id="coverHead"></th>
                    <th class="item" id="titleHead">Title</th>
                    <th class="item" id="genreHead">Genre</th>
                    <th class="item" id="platformHead">Platform</th>
                    <th class="item" id="developerHead">Developer</th>
                    <th class="item"></th>
                </tr>
            </table>
        </div>
        <div id="scroll">
            <table>
                <tr v-for="game in wishlist" id="bodyRows">
                    <td v-show="filterList(game)" class="cover"><img :src="game.thumbnail" alt="No picture available"></td>
                    <td v-show="filterList(game)" class="item">{{ game.title }}</td>
                    <td v-show="filterList(game)" class="item">{{ game.genre }}</td>
                    <td v-show="filterList(game)" class="item">{{ game.platform }}</td>
                    <td v-show="filterList(game)" class="item">{{ game.developer }}</td>
                    <td v-show="filterList(game)" class="item">
                        <v-btn @click="viewGame(game.id)" class="btn" variant="outlined">View Game</v-btn>
                        <v-btn @click="addToWishlist(game.id)" class="btn" variant="outlined">Remove from Wishlist</v-btn>
                    </td>
                </tr>
            </table>
        </div>
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
    border-color: navy;
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
    font-size: 15px;
    font-family: Arial;

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
    align-self: center;
}

#scroll {
    overflow-y: scroll;
    height: 750px;
}

#headerRow {
    padding: 10px;
    background-color: steelblue;
}

tr {
    background-color: lightblue;
}

#tableBackground {
    background-color: steelblue;
    height: 850px;
}

#titleHead {
    padding-left: 30px;
}

#genreHead {
    padding-left: 25px
}

#platformHead {
    padding-left: 15px;
}

#developerHead {
    padding-left: 5px;
}</style>