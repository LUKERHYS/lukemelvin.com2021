<template>
    <div class="grid-container">
        <img class="grid-item" src="https://cms.lukemelvin.com/uploads/medium_COMP_1_a86ede41ec.jpeg">
    </div>
</template>

<script>
export default {
  name: 'Gallery',
  props: ['imageURLS'],
  data() {
    return {
      images: [],
    };
  },
  mounted() {
    fetch('https://cms.lukemelvin.com/portfolios')
      .then((res) => res.json())
      .then((payload) => { this.images = payload; });
  },
};
</script>

<style lang="scss" scoped>
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
