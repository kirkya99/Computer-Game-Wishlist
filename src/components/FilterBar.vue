<script>

export default {
    emits: ['filterGames'],
    data() {
        return {
            selectedTitle: '',
            selectedGenre: '',
            selectedPlatform: '',
            selectedDeveloper: '',
            genres: ['All', 'Action RPG', 'ARPG', 'Battle Royale', 'Card Game',
                'Fighting', 'MMOARPG', 'MMOFPS', 'MMORPG', 'MMO', 'MOBA', 'Racing', 'Shooter', 'Social', 'Sports', 'Strategy'],
            platforms: ['All', 'PC (Windows)', 'Web Browser']
        }
    },
    methods: {
        filterGamesList() {
            if(this.selectedGenre === 'All') {
                this.selectedGenre = ''
            }
            if(this.selectedPlatform === 'All') {
                this.selectedPlatform = ''
            }
            this.$emit('filterGames', this.selectedTitle, this.selectedGenre, this.selectedPlatform, this.selectedDeveloper)
        },
        resetFilter() {
            this.selectedTitle = ''
            this.selectedGenre = ''
            this.selectedPlatform = ''
            this.selectedDeveloper = ''
            this.filterGamesList()
        } 
    }
}
</script>

<template>
    <div class="flex-container">
        <div>
            <v-text-field label="Filter Title" v-model="selectedTitle" variant="outlined" class="input" bg-color="blue-darken-2"></v-text-field>
        </div>
        <div>
            <v-autocomplete label="Filter Genre" :items="genres" variant="outlined" v-model="selectedGenre"
                class="input" bg-color="blue-darken-2"></v-autocomplete>
        </div>
        <div>
            <v-autocomplete label="Filter Platform" :items="platforms" variant="outlined" v-model="selectedPlatform"
                class="input" bg-color="blue-darken-2"></v-autocomplete>
        </div>
        <div>
            <v-text-field label="Filter Developer" v-model="selectedDeveloper" variant="outlined" class="input" bg-color="blue-darken-2"></v-text-field>
        </div>
        <div id="buttons">
            <v-btn @click="filterGamesList" class="input-btn" variant="outlined" color="white">Apply Filter</v-btn>
            <v-btn @click="resetFilter" class="input-btn" variant="outlined" color="white">Reset Filter</v-btn>
        </div>
    </div>
</template>

<style scoped>
h1 {
    text-align: center;
}

.flex-container {
    display: flex;
    flex-wrap: nowrap;
    width: 100%;
    background-color: steelblue;
    margin-top: 10px;
    margin-bottom: 10px;

}

.flex-container>div {
    width: 20%;
    background-color: steelblue;
    margin-top: 15px;
}

.input {
    width: 95%;
    margin: auto;
    margin-top: auto;
}
.input-btn {
    width: 95%;
    margin: 1%;
}
#buttons {
    margin: auto;
}</style>