<template>
<div class="align-container">
  <div :for="(url, index) in urls" class="grid-container">
    <img :key="index" :src="preUrl + url">
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
      urls: [],
    };
  },
  mounted() {
    fetch('https://cms.lukemelvin.com/upload/files')
      .then((res) => res.json())
      .then((payload) => {
        payload.forEach((image) => {
          this.urls.push(image.url);
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
.grid-container {
  max-width: 75vw;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;
  gap: 2em 2em;
  grid-template-areas:
    ". . ."
    ". . ."
    ". . .";
}
</style>
