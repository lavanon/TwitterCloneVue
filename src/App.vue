<script>
<script>    
    import NavBar from './components/NavBar.vue'

    export default {
        name: 'app',
        components: { },
        components: { NavBar},
        data() {
            return {
            search: 'tesla',
            apiData: [],
            }
        },
        mounted() {
            fetch(`https://api.parsely.com/v2/search?apikey=arstechnica.com&q=${this.search}&days=30`)
            .then(res => res.json())
            .then(data => this.apiData = data.data)
        },
        methods: {
            activateSearch() {
                fetch(`https://api.parsely.com/v2/search?apikey=arstechnica.com&q=${this.search.replace(/[^\w\s]/gi, '')}&days=${this.selected}`)
                .then(res => res.json())
                .then(data => this.apiData = data.data)
            }
        }
    }
</script>


<template>
 <NavBar/>
    <div id="searchButton" class="ui fluid action input">
        <input type="text" v-on:keyup.enter="activateSearch" v-model="search" placeholder="Search...">
        <div @click="activateSearch" class="ui button">Search</div>
        <select class="dropdown" v-model="selected" @change="activateSearch">
            <option  disabled value="">Adjust time span</option>
            <option value="1">Today</option>
            <option value="7" >This Week</option>
            <option value="30">This Month</option>
            <option value="365">This Year</option>
        </select>
    </div>
    <div id="article" class="ui comments" v-for="(item, index) in apiData" :key="index">
        <div class="comment">
            <a class="avatar">
                <img id="img" :src="item.image_url" >
            </a>
            <div class="content">
                <a :href="item.url" target="blank" class="author">{{item.title}}</a>
                <div class="metadata">
                    <span class="date">{{item.pub_date}}</span>
                </div>
                <div class="text">
                    {{item.author}}
                </div>
            </div>
        </div>
    </div>
</template>



<style>
    #img {
        height: 30px;
        width:30px;
    }
    #searchButton {
        padding: 20px;
    }
    #article {
        padding-left: 20px;
        max-width:750px;
    }
</style>
