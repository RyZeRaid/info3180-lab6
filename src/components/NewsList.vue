<template>
    <form @submit.prevent="searchNews" class="d-flex flex-column justify-content-center">
 <div class="input-group mx-sm-3 mb-2">
 <label class="visually-hidden" for="search">Search</label>
 <input type="search" name="search" v-model="searchTerm"
id="search" class="form-control mb-2 mr-sm-2" placeholder="Enter
 search term here" />
 <button class="btn btn-primary mb-2">Search</button>
 </div>
 <p>You are searching for {{ searchTerm }}</p>
 </form>

<div class="container_view">
    <div class="card" v-for="article in articles" style="width: 20rem; height: 30rem;">
        <img class="card-img-top" :src=" article.urlToImage " alt="News Image" style="height: 10rem">

        <div class="card-body">
            <h5 class="card-title">{{ article.title }}</h5> 
            <p class="card-text">{{ article.description }}</p>
        </div>
    </div>
</div>
    
    
</template>

<script>
export default {
 data() {
 return {
 articles: [],
 searchTerm : ''
 }
 },
 
 created() {
     let self = this;

 fetch('https://newsapi.org/v2/top-headlines?country=us',
{
 headers: {
 'Authorization': `Bearer ${import.meta.env.VITE_NEWSAPI_TOKEN}`
 }
})
 .then(function(response) {
 return response.json();
 })
 .then(function(data) {
 console.log(data);
 self.articles = data.articles;
 });
 },
 methods: {
 searchNews() {
 let self = this;
 console.log(self.searchTerm)
 fetch('https://newsapi.org/v2/everything?q='+ self.searchTerm + '&language=en', {
 headers: {
 'Authorization': `Bearer ${import.meta.env.VITE_NEWSAPI_TOKEN}`,
 }
})
 .then(function(response) {
 return response.json();
 })
 .then(function(data) {
 console.log(data);
 self.articles = data.articles;
 });
 }
 }
 
};
</script>

<style>
    .card{
        margin: 10px;
    }

      .container_view {
    max-width: 100%;
    flex-wrap: wrap;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>