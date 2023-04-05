<template>
  <NavBar title="My App" />
  <FeedContent :articles-data="articlesData" @update-articles="articlesData = $event" />
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
  data() {
    return {
      articlesData: [],
    }
  },
  created(){
    this.fetchArticles();
  },
  methods: {
    async fetchArticles() {
      const apiKey = process.env.NEWS_KEY;
      const query = '';
      const date = new Date(new Date().valueOf() - 1000 * 60 * 60 * 24).toISOString().slice(0, 10);
      const url = `https://newsapi.org/v2/everything?q=${query || 'japan'}&from=${date}&sortBy=popularity&apiKey=${apiKey}`;
      const response = await fetch(url);
      const data = await response.json();
      this.articlesData = data.articles;
      console.log(url);
      console.log('fetched data:', data);
    },
  },
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
    filter:invert(1);
    background-color: #eeeeee;
    color: #272a2e;
    .article, .search {
      filter: invert(1);
      background-color: $light-gray;
      color: $black;
    }
    ::placeholder {
      color: $black;
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
