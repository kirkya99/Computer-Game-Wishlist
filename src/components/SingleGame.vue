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
    updated() {
        this.currentGameIndex = this.gameIndex
    },
    computed: {
        currentGame() {
            return this.games[this.gameIndex]
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
            <div id="returnBtn">
                <v-btn @click="quitView" variant="outlined" class="btn">Return to List</v-btn>
            </div>
            <div v-if="games.length" class="text">
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
                <div id="openDeveloperPageBtn">
                    <v-btn variant="outlined" class="btn" @click="openDeveloperPage(currentGame.game_url)">Open developer
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

img {
    margin-left: auto;
    margin-right: auto;
}

#returnBtn {
    text-align: center;
    width: 50%;
    padding: 1%;
    margin-left: auto;
    margin-right: auto;
}

.btn {
    text-align: center;
    width: 60%;
    margin-left: auto;
    margin-right: auto;
}

.text {
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

#openDeveloperPageBtn {
    margin: 5%;
    text-align: center;
    ;
}
</style>