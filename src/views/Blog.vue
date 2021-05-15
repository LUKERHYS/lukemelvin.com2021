<template>
  <div>
    <article-grid/>
  </div>
</template>

<script>
import articleGrid from '../components/ArticleGrid.vue';

export default {
  name: 'blog',
  components: {
    'article-grid': articleGrid,
  },
};
</script>

<style lang="sass" scoped>

</style>
