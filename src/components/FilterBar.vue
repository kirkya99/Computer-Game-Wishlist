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
        }
    }
}
</script>

<template>
    <div>
        <label>Title: </label>
        <input v-model="selectedTitle">
        <label>Genre: </label>
        <input v-model="selectedGenre">
        <label>Platform: </label>
        <input v-model="selectedPlatform">
        <label>Developer: </label>
        <input v-model="selectedDeveloper">

        <t-select placeholder="genres" :options="genres"></t-select>
        <v-text-field clearable label="Game Title" v-model="selectedTitle"></v-text-field>
        <v-autocomplete clearable label="Autocomplete"
            :items="genres"
            v-model="selectedGenre"></v-autocomplete>
        <v-autocomplete clearable label="Autocomplete" :items="platforms"
            v-model="selectedPlatform"></v-autocomplete>
        <v-text-field clearable label="Game Developer" v-model="selectedDeveloper"></v-text-field>
        <v-btn @click="filterGamesList">Apply Filters</v-btn>
        <button @click="filterGamesList">Apply Filters</button>
    </div>
</template>

<style scoped>
h1 {
    text-align: center;
}

div {
    margin-top: 10px;
    margin-bottom: 10px;
    border: dotted;
    height: 75px
}
</style>