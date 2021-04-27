<template>
  <div class="container grid grid-cols-3 gap-4">
    <div v-for="data in articles" :key="data.id" class="cursor-pointer" @click="onClick(data.slug)">
      <h1 class="font-bold text-xl">{{data.title}}</h1>
      <img :src="`http://localhost:1337${data.image.url}`" alt="Image">
      <p class="text-sm text-gray-600">{{data.description}}</p>
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
  methods:{
    onClick(slug){
      this.$router.push({
        path:`/${slug}`
      })
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
