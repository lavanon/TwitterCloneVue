<script>
    export default {
        name: 'app',
        components: { },
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
                fetch(`https://api.parsely.com/v2/search?apikey=arstechnica.com&q=${this.search}&days=30`)
                .then(res => res.json())
                .then(data => this.apiData = data.data)
            }
        }
    }
</script>


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
/* #app {
    padding: 0.5rem;
    background: #f8f9fa;
    color: #495057;
    border: 1px solid #dee2e6;
    border-radius: 6px;
}
#item {
      display: flex;
    align-items: center;
    flex-wrap: wrap;
} */
#img {
  height: 30px;
  width:30px;
}
#searchButton {
  padding-bottom: 10px;
}
</style>
