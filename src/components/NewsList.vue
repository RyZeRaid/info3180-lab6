<template>
    <div class="card" v-for="article in articles" style="width: 20rem; height: 30rem;">
        <img class="card-img-top" :src=" article.urlToImage " alt="News Image" style="height: 10rem">

        <div class="card-body">
            <h5 class="card-title">{{ article.title }}</h5> 
            <p class="card-text">{{ article.description }}</p>
        </div>
    </div>
    
</template>

<script>
export default {
 data() {
 return {
 articles: []
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
 }
};
</script>

<style>
    .card{
        margin: 10px;
    }
</style>