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
        },
        filterList(game) {
            let boolTitle = false;
            let boolGenre = false;
            let boolPlatform = false;
            let boolDeveloper = false;
            let boolean;
            let title = game.title.toLowerCase();
            let genre = game.genre.toLowerCase();
            let platform = game.platform.toLowerCase();
            let developer = game.developer.toLowerCase();
            if (this.filterTitle.localeCompare("") == 0) {
                boolTitle = true;
            }
            else {
                if (title.includes(this.filterTitle)) {
                    boolTitle = true;
                }
            }

            if (this.filterGenre.localeCompare("") == 0) {
                boolGenre = true;
            }
            else {
                if (genre.includes(this.filterGenre)) {
                    boolGenre = true;
                }
            }

            if (this.filterPlatform.localeCompare("") == 0) {
                boolPlatform = true;
            }
            else {
                if (platform.includes(this.filterPlatform)) {
                    boolPlatform = true;
                }
            }

            if (this.filterDeveloper.localeCompare("") == 0) {
                boolDeveloper = true;
            }
            else {
                if (developer.includes(this.filterDeveloper)) {
                    boolDeveloper = true;
                }
            }

            boolean = boolTitle && boolGenre && boolPlatform && boolDeveloper;
            return boolean;
        },
        receiveFilter(title, genre, platform, developer) {
            this.filterTitle = title.toLowerCase();
            this.filterGenre = genre.toLowerCase();
            this.filterPlatform = platform.toLowerCase();
            this.filterDeveloper = developer.toLowerCase();
        }
    },
    components: {
        FilterBar
    },
    data() {
        return {
            filterTitle: "",
            filterGenre: "",
            filterPlatform: "",
            filterDeveloper: ""
        }
    }
}
</script>

<template>
    <FilterBar></FilterBar>
    <table>
        <tr id="headerRow">
            <th class="cover">Cover</th>
            <th class="item">Title</th>
            <th class="item">Genre</th>
            <th class="item">Platform</th>
            <th class="item">Developer</th>
            <th class="item"></th>
        </tr>
    </table>
    <div id="scroll">
        <table>
            <tr v-for="game in games">
                <td v-if="filterList(game)" class="cover"><img :src="game.thumbnail" alt="No picture available"></td>
                <td v-if="filterList(game)" class="item">{{ game.title }}</td>
                <td v-if="filterList(game)" class="item">{{ game.genre }}</td>
                <td v-if="filterList(game)" class="item">{{ game.platform }}</td>
                <td v-if="filterList(game)" class="item">{{ game.developer }}</td>
                <td v-if="filterList(game)" class="item">
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
    align-self: center;
}

#scroll {
    overflow-y: scroll;
    height: 625px;
}

#headerRow {
    padding: 10px;
    background-color: steelblue;
}

tr {
    background-color: lightblue;
}
</style>