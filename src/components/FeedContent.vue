<template>
    <div class="articles">
      <ArticleCard
        v-for="(article, index) in articles"
        :key="index"
        :title="article.title"
        :media="article.media"
        :summary="article.summary"
        :rights="article.rights"
        :link="article.link"
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
            media: article.media || 'https://media.istockphoto.com/id/1309699912/vector/vector-illustration-daily-news-paper-template-with-text-and-picture-placeholder.jpg?s=1024x1024&w=is&k=20&c=H-sG8enS-3H7cFcJaLY883g4UbUBN0zNxrQkl2OzjYM=',
            summary: article.summary || 'No description',
            rights: article.rights || 'Uknown',
            link: article.link || '',
          }))
      },
    },
  };
  </script>
  
<style lang="scss">
    @import "../styles/_variables.scss";
    .articles {
        display: flex;
        flex-direction: column;
        gap: 8px;
        margin-top: 116px;
        align-self: center;
        width: 90%;
        max-width: 500px;
    }
    @media screen and (min-width: 800px) {
        .articles {
            max-width: 1000px;
            display: grid;
            grid-template-columns: repeat(2, 1fr);
        }
    }
    @media screen and (min-width: 1100px) {
        .articles {
            max-width: 1100px;
            grid-template-columns: repeat(3, 1fr);
        }
    }
</style>
  