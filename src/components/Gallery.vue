<template>
<div class="align-container">
  <div class="masonry-with-columns">
    <img
    v-for="image in this.images"
    :key="image.image.id"
    :src="preUrl + image.image.url"
    :alt="image.image.alternativeText">
  </div>
</div>
</template>

<script>
export default {
  name: 'Gallery',
  props: [],
  data() {
    return {
      preUrl: 'https://cms.lukemelvin.com',
      images: [],
    };
  },
  mounted() {
    fetch('https://cms.lukemelvin.com/folio-images')
      .then((res) => res.json())
      .then((payload) => {
        payload.forEach((image) => {
          if (image.publish === true) {
            this.images.push(image);
          }
        });
      });
  },
};
</script>

<style lang="scss" scoped>
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
