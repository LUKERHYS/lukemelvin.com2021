<template>
    <div>
        <h1>This is my photography portfolio</h1>
        <gallery />
    </div>
</template>

<script>
import Gallery from '../components/Gallery.vue';

export default {
  name: 'Portfolio',
  components: {
    Gallery,
  },
  props: ['image-urls'],
};
</script>

<style lang="scss" scoped>

</style>
