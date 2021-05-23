<template>
<!-- <div class="align-container"> -->
  <!-- <div class="masonry-with-columns"> -->
    <div class="post-content">
      <div :style="textLimit" class="blog-item" v-for="blogPost in this.blogPosts" :key="blogPost.id">
        <h1>{{ blogPost.postTitle }}</h1>
        <p>{{ blogPost.postContent }}</p>
      </div>
      <button @click="readMoreLess">{{ moreOrLess }}</button>
    </div>
  <!-- </div> -->
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
      readMore: false,
      textLimit: {
        width: '30vw',
        height: '30vh',
      },
      moreOrLess: 'More'
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
    }
  }
};
</script>

<style lang="scss" scoped>
div {
  // border: solid red 1px;
}
.align-container {
  display: flex;
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
.post-content {
  overflow: hidden;
  padding: 1em;
}
</style>
