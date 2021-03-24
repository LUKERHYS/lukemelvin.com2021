<template>
<div class="welcome-banner">
  <p>Hello, Welcome!</p>
  <p>Anyway, enough about me, Lets talk about you and
    what you need help with {{ this.services }}</p>
</div>
</template>

<script>
export default {
  name: 'Welcome',
  data() {
    return {
      services: ['Photo', 'Web', 'Design'],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
