<script>
export const gamesTab = 0;
export const wishlistTab = 1;

export default {
    emits: ['filterWishList'],
    methods: {
        switchToGamesList() {
            this.$emit('filterWishList', gamesTab);
            document.getElementById('gameslist').style.bold
        },
        switchToWishlist() {
            this.$emit('filterWishList', wishlistTab);
        }
    }
}
</script>

<template>
    <div id="header">
        <div class="header_bar">
            <div class="header_item" role="button" id="gameslist" @click="switchToGamesList">
                <h2>All Games</h2>
            </div>
            <div class="header_item" role="button" id="wishlist" @click="switchToWishlist">
                <h2>Wishlist</h2>
            </div>
        </div>
    </div>
</template>

<style scoped>
* {
    font-family: Arial;
}

#header {
    /*width: 100%;*/
    width: 100%;
    background-color: lightblue;
}

.header_bar {
    display: flex;
    background-color: dodgerblue;
}

.header_item {
    width: 50%;
    text-align: center;
}

#gameslist:hover {
    background-color: lightblue;
}

#wishlist:hover {
    background-color: lightblue;
}

h2:hover {
    cursor: pointer;
}</style>