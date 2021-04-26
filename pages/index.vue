<template>
  <div class="container">
    <div v-for="data in articles" :key="data.id">
      <h1>{{data.title}}</h1>
      <img :src="`http://localhost:1337${data.image.url}`" alt="Image">
      <p>{{data.description}}</p>
    </div>
  </div>
</template>

<script>
import queryArticles from "~/apollo/query/queryArticles"
export default {
  data(){
    return{
      articles:[]
    }
  },
  apollo: {
    articles: {
      prefetch: true,
      query: queryArticles
    }
  }
}
</script>
