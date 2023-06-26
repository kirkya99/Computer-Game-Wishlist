<script>
export const prev = 0;
export const next = 1;

export default {
    props: ['gameIndex', 'games'],
    emits: ['returnToList'],
    data() {
        return {
            currentGameIndex: this.gameIndex
        }
    },
    created() {
        this.currentGameIndex = this.gameIndex
    },
    computed: {
        currentGame() {
            return this.games[this.currentGameIndex]
        }
    },
    methods: {
        quitView() {
            this.$emit('returnToList')
        },
        nextGame() {
            if (this.currentGameIndex + 1 < this.games.length) {
                this.currentGameIndex = this.currentGameIndex + 1
            }
        },

        prevGame() {
            if (this.currentGameIndex != 0) {
                this.currentGameIndex = this.currentGameIndex - 1
            }
        },
        openDeveloperPage(url) {
            window.open(url, '_blank')
        }
    }
}

</script>

<template>
    <div id="backgroundPage">
        <div id="page">
            <div class="headerBar">
                <div id="leftButton">
                    <v-btn @click="prevGame" variant="outlined" color="black" class="btn">Previous Game</v-btn>
                </div>
                <div id="middleButton">
                    <v-btn @click="quitView" variant="outlined" color="black" class="btn">Return to List</v-btn>
                </div>
                <div id="rightButton">
                    <v-btn @click="nextGame" variant="outlined" color="black" class="btn">Next Game</v-btn>
                </div>
            </div>
            <div v-if="games.length" class="gameDetails">

                <div class="meta">

                    <h2>{{ currentGame.title }}</h2>
                    <img :src="currentGame.thumbnail" alt="No Picture available" />
                </div>
                <div class="flex">
                    <div class="info">
                        <p><b>Genre:</b> {{ currentGame.genre }}</p>
                        <p><b>Platform:</b> {{ currentGame.platform }}</p>
                    </div>
                    <div class="info">
                        <p><b>Release Date:</b> {{ currentGame.release_date }}</p>
                        <p><b>Developer:</b> {{ currentGame.developer }}</p>
                        <p><b>Publisher:</b> {{ currentGame.publisher }}</p>
                    </div>
                </div>
                <div class="description">
                    <p><b>Game Description:</b></p>
                    <p>{{ currentGame.short_description }}</p>
                </div>
                <div id="site">
                    <v-btn color="blue" class="btn" @click="openDeveloperPage(currentGame.game_url)">Open developer
                        page</v-btn>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
#backgroundPage {
    height: 967px;
}

#page {
    margin-bottom: 0px;
    height: 95%;
    background-color: lightblue;
    width: 60%;
    margin-left: auto;
    margin-right: auto;
}

.headerBar {
    display: flex;
    padding: 1%;
    width: 100%;
    margin-left: auto;
    margin-right: auto;
}

img {
    margin-left: auto;
    margin-right: auto;
}

#leftButton {
    text-align: left;
    width: 100%;
}

#middleButton {
    text-align: center;
    width: 100%;
}

#rightButton {
    text-align: right;
    width: 100%;
}

.btn {
    width: 50%;
}

.gameDetails {
    width: 60%;
    margin-left: auto;
    margin-right: auto;
}

.meta {
    width: 100%;
    text-align: center;
}

.flex {
    display: flex;
    width: 80%;
    margin-left: auto;
    margin-right: auto;
}

.info {
    width: 100%;
}

.description {
    width: 80%;
    margin-left: auto;
    margin-right: auto;
}

.meta>img {
    margin: 2.5%
}

#site {
    margin: 5%;
    text-align: center;
}
</style>