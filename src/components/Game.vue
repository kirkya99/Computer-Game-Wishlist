<script>
export const prev = 0;
export const next = 1;

export default {
    props: ['gameIndex', 'games'],
    emits: ['returnToList'],
    data(){
        return{
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
            if(this.currentGameIndex + 1 < this.games.length)
            {
                this.currentGameIndex = this.currentGameIndex + 1
            }
        },

        lastGame() {
            if (this.currentGameIndex != 0) {
                this.currentGameIndex = this.currentGameIndex - 1
            }
        }
    }
}

</script>

<template>
    <div id="page">
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
            
            <p>Page {{ currentGameIndex+1 }} of {{ games.length }}</p>
        </div>
    </div>
    <v-btn @click="lastGame">Previous Game</v-btn>
    <v-btn @click="nextGame">Next Game</v-btn>
    <v-btn @click="quitView">Return to List</v-btn>
</template>