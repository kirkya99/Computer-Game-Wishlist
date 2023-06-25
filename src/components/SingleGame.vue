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
        }
    }
}

</script>

<template>
    <div id="backgroundPage">
        <div id="page">
            <div class="headerBar">
                <v-btn @click="prevGame" color="blue">Previous Game</v-btn>
                <v-btn @click="quitView" color="blue">Return to List</v-btn>
                <v-btn @click="nextGame" color="blue">Next Game</v-btn>
            </div>
            <div v-if="games.length">
                <div class="gameDetails">
                    <h2>{{ currentGame.title }}</h2>
                    <img :src="currentGame.thumbnail" alt="No Picture available" />
                    <p>Developer: {{ currentGame.developer }}</p>
                    <p>Publisher: {{ currentGame.publisher }}</p>
                    <p>Release Date: {{ currentGame.release_date }}</p>
                    <p>{{ currentGame.short_description }}</p>
                    <a :href="currentGame.game_url" target="_blank" rel="noreferrer noopener">Open Game Webpage</a>
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
.headerBar{
    padding: 1%;
    width: 98%;
}
v-btn{
    width: 33%;
}
</style>