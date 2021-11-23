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


<div class="ui comments" v-for="(item, index) in apiData" :key="index">
  <div class="comment">
    <a class="avatar">
      <img id="img" :src="item.image_url" >
    </a>
    <div class="content">
      <a class="author">Tom Lukic</a>
      <div class="text">
        This will be great for business reports. I will definitely download this.
      </div>
      <div class="actions">
        <a class="reply">Reply</a>
        <a class="save">Save</a>
        <a class="hide">Hide</a>
        <a>
          <i class="expand icon"></i>
          Full-screen
        </a>
      </div>
    </div>
  </div>
</div>
  <!-- <div id="app" class="ui comments" v-for="(item, index) in apiData" :key="index">
    <a class="avatar">
      <img id="img" :src="item.image_url" >
    </a>
    <div class="content">
      <a class="author">{{item.title}}</a>
      <div class="metadata">
        <span class="date">{{item.pub_date}}</span>
      </div>
      <div class="text">
        {{item.author}}
      </div>
      <div class="actions">
        <a class="reply">Reply</a>
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
  </div> -->
<!-- <div id="app" v-for="(item, index) in apiData" :key="index">
  <ul id="item" >
    <li><img id="img" :src="item.image_url" ></li>
    
    <li>{{index}}. {{item.title}}</li>
    <li>{{item.pub_date}} </li>
    </ul>
</div> -->
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
