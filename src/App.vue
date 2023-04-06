<template>
  <NavBar :query="query" @search="fetchArticles" />
  <FeedContent visibleArticles :articles-data="articlesData" @update-articles="articlesData = $event" />
  <p class="see-more" @click="addArticles">See more</p>
</template>

<script>
import FeedContent from './components/FeedContent.vue';
import NavBar from './components/NavBar.vue'

export default {
  name: 'App',
  components: {
    FeedContent,
    NavBar
  },
  props: {
    visibleArticles: {
      type: Number,
      default: 10,
    },
    query: {
    type: String,
    default: 'japan'
  }
  },
  data() {
    return {
      articlesData: [],
      pageSize: 10
    }
  },
  created(){
    this.fetchArticles(this.query);
  },
  methods: {
    async fetchArticles(query , pageSize=10) {
      const apiKey = process.env.VUE_APP_NEWS_KEY;
      const date = new Date(new Date().valueOf() - 1000 * 60 * 60 * 24).toISOString().slice(0, 10);
      const url = `https://newsapi.org/v2/everything?q=${query || 'japan'}&from=${date}&sortBy=popularity&apiKey=${apiKey}`;
      const response = await fetch(url);
      const data = await response.json();
      this.articlesData = data.articles.slice(0,pageSize);
      console.log('Data fetched from API');
    },
      addArticles() {
          const searchQuery = document.querySelector('.search').value;
          this.pageSize = this.pageSize + 10;
          this.fetchArticles(searchQuery || this.query, this.pageSize);
      }
    }
}
</script>


<style lang="scss">
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: #272a2e;
  color: #eeeeee;
  transition: 200ms;
  &.light {
    // filter:invert(1);
    background-color: #eeeeee;
    color: #272a2e;
    .navbar {
      background-color: #eeeeee;
      .top {
        h3 {
          color: #272a2e;
        }
        svg {
          color: #272a2e;
        }
      }
    }
    .article, .search {
      background-color: $light-gray;
      color: $black;
    }
    ::placeholder {
      color: $black;
    }
  }
  .see-more {
    margin-bottom: 60px;
    &:hover{
      cursor: pointer;
    }
  }
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
</style>
