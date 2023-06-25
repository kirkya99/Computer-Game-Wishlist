<script>

export default {
    emits: ['filterGames'],
    data() {
        return {
            selectedTitle: '',
            selectedGenre: '',
            selectedPlatform: '',
            selectedDeveloper: '',
            genres: ['Action RPG', 'ARPG', 'Battle Royale', 'Card Game',
                'Fighting', 'MMOARPG', 'MMOFPS', 'MMORPG', 'MMO', 'MOBA', 'Racing', 'Shooter', 'Social', 'Sports', 'Strategy'],
            platforms: ['PC (Windows)', 'Web Browser']
        }
    },
    methods: {
        filterGamesList() {
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
            <v-text-field label="Game Title" v-model="selectedTitle" variant="outlined" class="input" bg-color="blue-darken-2"></v-text-field>
        </div>
        <div>
            <v-autocomplete label="Autocomplete" :items="genres" variant="outlined" v-model="selectedGenre"
                class="input" bg-color="blue-darken-2"></v-autocomplete>
        </div>
        <div>
            <v-autocomplete label="Autocomplete" :items="platforms" variant="outlined" v-model="selectedPlatform"
                class="input" bg-color="blue-darken-2"></v-autocomplete>
        </div>
        <div>
            <v-text-field label="Game Developer" v-model="selectedDeveloper" variant="outlined" class="input" bg-color="blue-darken-2"></v-text-field>
        </div>
        <div>
            <v-btn @click="filterGamesList" class="input" bg-color="blue-darken-2">Apply Filter</v-btn>
            <v-btn @click="resetFilter" class="input" bg-color="blue-darken-2">Reset Filter</v-btn>
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
    width: 350px;
    margin: auto;
    margin-top: auto;
}
v-btn {
    margin-top: 10px;
    margin-bottom: 10px;
}</style>