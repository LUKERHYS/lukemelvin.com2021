<template>
<div class="align-container">
  <div class="masonry-with-columns">
    <img
    v-for="image in this.images"
    :key="image.id"
    :src="preUrl + image.url"
    :alt="image.alternativeText">
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
    fetch('https://cms.lukemelvin.com/upload/files')
      .then((res) => res.json())
      .then((payload) => {
        payload.forEach((image) => {
          this.images.push(image);
        });
      });
  },
};
</script>

<style lang="scss" scoped>
div {
  border: solid red 1px;
}
.align-container {
  display: flex;
  justify-content: center;
}
.masonry-with-columns {
  max-width: 90vw;
  columns: 6 200px;
  column-gap: 1rem;
  div {
    width: 150px;
    background: #EC985A;
    color: white;
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
