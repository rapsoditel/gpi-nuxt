<template>
  <div class="px-10">
      <div class="mx-auto grid gap-10" v-if="articles.length > 0">
          <h1 class="font-bold text-3xl">{{articles[0].title}}</h1>
           <img :src="`http://localhost:1337${articles[0].image.url}`" alt="Image">
           <div v-html="articles[0].content"></div>
      </div>
  </div>
</template>
<script>
import queryArticleDetail from "~/apollo/query/queryArticleDetail";
export default {
  name: "detail",
  data() {
    return {
      articles: [],
    };
  },
  apollo: {
    articles: {
      prefetch: true,
      query: queryArticleDetail,
      variables() {
        return { slug: this.$route.params.detail };
      },
    },
  },
};
</script>