

<script>

export default {
  name: 'App',
  components: {
    
  }
}


// async function search(query, days) {
// //     if (query.test(/\W/g)) {
// //         return console.log("please");
// //     }
//     if (query === null || query === undefined) {
//         return console.log("please enter something a little less hacky");
//     }
//     if (!Number(days)) {
//         return console.log("please enter a numbers")
//     }

//     let response = await
//     fetch(`https://api.parsely.com/v2/search?apikey=arstechnica.com&q=${query}&days=${days}`)
//     let data = await response.json()
//     return data;
// }

// search("apple", 1).then((data)=> console.log(data)) // output will be the required data


//JS
//Consume and show thew api data
  // going use the vue for render method to show the titles
  // using the h1, show the title 


// let dataset = {};

// dataset.map(data => {
//     title: data.Title;
//     image: data.image;
//     description: data.Tags;
//     publishDate: data.pushblishDate;
//     breadcrumb: data.parsely;
// })

Vue.createApp({
  data() {
    return {
      items: [{ message: 'Foo' }, { message: 'Bar' }]
    }
  }
}).mount('#array-rendering')
</script>


<template>
  <li id="array-rendering">
  <!-- <li v-for="item in items" :key="item.message"> -->
    {{ items }}
  <!-- </li> -->
</li>
</template>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
