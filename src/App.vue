<script>    
    import NavBar from './components/NavBar.vue'

    export default {
        name: 'app',
        components: { NavBar},
        data() {
            return {
            search: 'tesla',
            apiData: [],
            selected: 30
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
        },
    }

</script>


<template>
 <NavBar/>
 <h3 class="ui headers ">Search for Articles</h3>
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
     <h3 class="ui headers margin-bottom">Search Results</h3>

    <div id="article" 
        v-for="(item, index) in apiData" 
        :key="index"
        >
        <div>
            <a  style=" vertical-align: top; display: table-cell;">
                <img id="img" :src="item.image_url" >
            </a>
            <div style="vertical-align: top; display: table-cell;">
                <div class="ui label">{{item.section}}</div>
                <h4 class="headerMargin"><a :href="item.url" target="blank" class="author">{{item.title}}</a></h4>
                <div class="text">
                   <strong> By {{item.author}} </strong> | {{item.pub_date.split("T")[0]}}
                </div>
            </div>
        </div>
        <hr class="hrPadding">

    </div>
</template>


<style>
    .headers{
        margin-bottom: 0;
        padding-left: 20px;
    }
    #img {
        height: 100px;
        width:140px;
        margin-right: 20px;
        object-fit: cover;
    }
    #searchButton {
        padding: 20px;
    }
    #article {
        padding-left: 20px;
        max-width:750px;
    }
    .dropdown {
        border: 1px solid lightgray;
        margin-left: 10px;
    }

    .headerMargin {
        margin-top: 10px;
    }
    .hrPadding{
        margin: 20px 0;
    }
    .margin-bottom {
        margin-bottom: 20px;
    }
</style>
