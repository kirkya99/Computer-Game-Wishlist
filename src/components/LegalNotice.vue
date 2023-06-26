<script>
export default {
    methods: {
        openRepository() {
            window.open('https://github.com/kirkya99/Computer-Game-Wishlist', '_blank')
        },
        openAPI() {
            window.open('https://www.mmobomb.com/api', 'blank')
        }
    }
}
</script>

<template>
    <div id="legalNoticeTab">
        <div id="page">
            <div class="text">
                <h2>Our Team</h2>
                <div class="list">
                    <ul>
                        <li>Arjan Mavraj</li>
                        <li>Fabian Schotte</li>
                        <li>Mike Tabler</li>
                    </ul>
                </div>
                <h2>Our Project</h2>
                <p>This web application is the practical task for the lecture Graphical User Interfaces of the University of
                    Applied Sciences Ravensburg-Weingarten</p>
                <p>The task was to create a web application with the following criteria:</p>
                <div class="list">
                    <ul>
                        <li>it has to utilize the JavaScript-Framwork Vue 3</li>
                        <li>the data should be retrieved using a REST API</li>
                        <li>it should have at least four components</li>
                        <li>The application is to be deployed on a cloud server for testing</li>
                    </ul>
                </div>
                <h2>Links</h2>
                <p>Our used API was provided by MMOBomb.com and MMOBomb.com is the source of the used data as well as the
                    owner of the used API.</p>
                <div class="btn">
                    <v-btn @click="openAPI" variant="outlined" class="v-btn">Our used API</v-btn>
                </div>
                <p>Our source code can be reviewed on GitHub.</p>
                <div class="btn">
                    <v-btn @click="openRepository" variant="outlined" class="v-btn">Our Repository</v-btn>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
#legalNoticeTab {
    height: 967px;
}

#page {
    background-color: lightblue;
    width: 60%;
    height: 95%;
    margin-left: auto;
    margin-right: auto;
}

.text {
    padding-top: 1%;
    width: 60%;
    margin-left: auto;
    margin-right: auto;
}


.btn {
    margin-top: 1%;
    margin-bottom: 1%;
    margin-left: 1%;
}

.v-btn {
    width: 50%;
}

.list {
    padding-left: 3%;
}
</style>