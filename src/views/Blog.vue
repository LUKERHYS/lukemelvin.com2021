<template>
<!-- <div class="align-container">
  <div class="masonry-with-columns"> -->
  <div>
    <div v-for="blogPost in this.blogPosts" :key="blogPost.id">
      <h1>{{ blogPost.postTitle }}</h1>
      <p>{{ blogPost.postContent }}</p>
     </div>
  </div>
<!-- </div> -->
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
};
</script>

<style lang="scss" scoped>
div {
  // border: solid red 1px;
}
.align-container {
  display: flex;
  justify-content: center;
}
.masonry-with-columns {
  width: 75vw;
  columns: 3 200px;
  column-gap: .5rem;
  div {
    width: 100vw;
    margin: 0 1rem 1rem 0;
    display: inline-block;
    width: 100%;
    text-align: center;
    font-family: system-ui;
    font-weight: 900;
    font-size: 2rem;
  }
  @for $i from 1 through 36 {
    div:nth-child(#{$i}) {
      $h: (random(400) + 100) + px;
      height: $h;
      line-height: $h;
    }
  }
}
img {
  padding: 0;
  margin: 0;
  max-width: 100%;
  max-height: auto;
}
</style>
