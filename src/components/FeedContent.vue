<template>
    <div class="articles">
      <ArticleCard
        v-for="(article, index) in articles"
        :key="index"
        :title="article.title"
        :img="article.img"
        :desc="article.desc"
        :src="article.src"
        :url="article.url"
      />
    </div>
  </template>
  
  <script>
  import ArticleCard from './ArticleCard.vue';
  
  export default {
    name: 'FeedContent',
    components: {
      ArticleCard,
    },
    props: {
      articlesData: {
        type: Array,
        default: () => [],
      },
    },
    computed: {
      articles() {
        return this.articlesData
          .map(article => ({
            title: article.title || 'No title',
            img: article.urlToImage || 'https://media.istockphoto.com/id/1309699912/vector/vector-illustration-daily-news-paper-template-with-text-and-picture-placeholder.jpg?s=1024x1024&w=is&k=20&c=H-sG8enS-3H7cFcJaLY883g4UbUBN0zNxrQkl2OzjYM=',
            desc: article.description || 'No description',
            src: article.source.name || 'Uknown',
            url: article.url || '',
          }))
          .slice(0, 15);
      },
    },
  };
  </script>
  
  <style lang="scss">
  @import "../styles/_variables.scss";
  .articles {
    margin-top: 16px;
    align-self: center;
    width: 90%;
    max-width: 500px;
  }
  </style>
  