<template>
    <div class="article" @click="openUrl">
      <h3 class="title">{{ title }}</h3>
      <div :style="{ backgroundImage: `url(${img})` }" class="img"></div>
      <p class="desc">{{ desc }}</p>
      <p class="src">Source: {{ src }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ArticleCard',
    props: {
      title: {
        type: String,
        default: 'No title',
      },
      img: {
        type: String,
        default: 'https://media.istockphoto.com/id/1309699912/vector/vector-illustration-daily-news-paper-template-with-text-and-picture-placeholder.jpg?s=1024x1024&w=is&k=20&c=H-sG8enS-3H7cFcJaLY883g4UbUBN0zNxrQkl2OzjYM=',
      },
      desc: {
        type: String,
        default: 'No description',
      },
      src: {
        type: String,
        default: 'Uknown',
      },
      url: {
        type: String,
        default: '',
      },
    },
    methods: {
      openUrl() {
        if (this.url) {
          window.open(this.url, '_blank');
        }
      },
    },
  };
  </script>

<style lang="scss">
@import "../styles/_variables.scss";
    .article {
        margin: 8px;
        padding: 2px 0;
        background-color: $gray;
        color: $white;
        border-radius: 12px;
        box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
        .title {
            text-align: start;
            font-size: 18px;
            padding: 0 16px;
        }
        .img {
            width: 100%;
            height: 200px;
            background-size: cover;
            background-position: center;
        }
        .desc {
            text-align: start;
            font-size: 14px;
            padding: 0 16px;
        }
        .src {
            text-align: right;
            font-size: 12px;
            padding-right: 16px;
        }
    }
</style>
