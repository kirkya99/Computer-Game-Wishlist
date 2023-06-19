<script>
import axios from 'axios'

export default{
    created(){
        axios.get('https://cors-anywhere.herokuapp.com/https://www.mmobomb.com/api1/games')
            .then(response => {
                console.log(response.data)
            })
            .catch(console.error)
    },
    props: ['selectedTab'],
    components:{
        axios
    },
    data(){
        return{
            gamesArray: []
        }
    },   
}

    
</script>

<template>

    {{ selectedTab }}
</template>