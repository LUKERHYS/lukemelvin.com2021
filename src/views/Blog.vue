<template>
<div class="grid">
  <div class="blog-item" v-for="blogPost in this.blogPosts" :key="blogPost.id">
    <div :style="textLimit" class="post-content">
      <h1>{{ blogPost.postTitle }}</h1>
      <p>{{ blogPost.postContent }}</p>
    </div>
    <div>
      <button @click="readMoreLess">{{ moreOrLess }}</button>
    </div>
  </div>
</div>
</template>

<script>
// import articleGrid from '../components/ArticleGrid.vue';

export default {
  name: 'blog',
  components: {
    // 'article-grid': articleGrid,
  },
  props: [],
  data() {
    return {
      preUrl: 'https://cms.lukemelvin.com',
      blogPosts: [],
      readMore: false,
      textLimit: {
        width: '30vw',
        height: '30vh',
      },
      moreOrLess: 'More',
    };
  },
  mounted() {
    fetch('https://cms.lukemelvin.com/blog-posts')
      .then((res) => res.json())
      .then((payload) => {
        payload.forEach((post) => {
          if (post.published === true) {
            this.blogPosts.push(post);
          }
        });
      });
  },
  methods: {
    readMoreLess() {
      // this.readMore = !this.readMore;
      if (this.textLimit.width === '30vw' && this.textLimit.height === '30vh') {
        this.textLimit.width = 'auto';
        this.textLimit.height = 'auto';
        this.moreOrLess = 'Less';
      } else {
        this.textLimit.width = '30vw';
        this.textLimit.height = '30vh';
        this.moreOrLess = 'More';
      }
    },
  },
};
</script>

<style lang="scss" scoped>
div {
  border: solid red 1px;
}
.grid {
  display: flex;
}
.blog-item {
  display: block;
  margin:  1%;
}
img {
  padding: 0;
  margin: 0;
  max-width: 100%;
  max-height: auto;
}
.post-content {
  overflow: hidden;
  padding: 1em;
}
</style>
