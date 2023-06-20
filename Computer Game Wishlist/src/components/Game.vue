<script>
export default {
    props: ['gameIndex', 'games'],
    emits: ['returnToList'],
    computed: {
        currentGame(){
            return this.games[this.gameIndex];
        }
    },
    methods: {
        quitView() {
            this.$emit('returnToList')
        },
        nextGame(){
            this.currentGameIndex = (this.currentGameIndex + 1) % this.gamesArray.length;
        },

        lastGame(){
            if(this.currentGameIndex != 0){
                this.currentGameIndex = this.currentGameIndex - 1;
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
                <p>{{ currentGame.short_description }}</p>
            </div>
        
        </div>
    </div>

    <p>Page:  {{ gameIndex+1 }}</p>












    <button @click="quitView">Return to List</button>
    
</template>