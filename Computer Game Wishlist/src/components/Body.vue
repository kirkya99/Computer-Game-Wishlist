<script>
export const listViewTab = 0;
export const singleGameViewTab = 1;

import List from './List.vue';
import Game from './Game.vue';

export default {
    props: ['selectedTab', 'games'],
    components: {
        List, Game
    },
    data() {
        return {
            selectedGameIndex: 0,
            wishlist: [],
            selectedView: listViewTab //0 = List, 1 = Single Game View
        }
    },
    methods: {
        showGame(gameId) {
            this.findGame(gameId);
            this.selectedView = singleGameViewTab;
        },
        findGame(gameId) {
            this.selectedGameIndex = 0
            while (gameId != this.games[this.selectedGameIndex].id) {
                this.selectedGameIndex++;
            }
        },
        showList() {
            this.selectedView = listViewTab
        }
    }
}
</script>

<template>
    <div v-if="selectedTab == 0">
        <div v-if="selectedView == 0">
            <List :games="games" @viewGame="showGame"></List>
        </div>
        <div v-if="selectedView == 1">
            <Game @returnToList="showList" :gameIndex="selectedGameIndex" :games="games"></Game>
        </div>
    </div>
    <div v-if="selectedTab == 1">
        <h2>Wunschliste</h2>
    </div>
</template>

