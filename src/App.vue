<template>
<div class="body">
    <div class="contianer">
      <div id="header" class="main">
        <h1>LukeMelvin.</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/portfolio">Portfolio</router-link> |
            <router-link to="/about">About</router-link>
        </div>
      </div>
    </div>
    <div id="app">
      <router-view/>
    </div>
</div>
</template>
<style lang="scss">
body{
    margin: 0px;
    padding: 0;
    background-color: #ffffff;
    width:100vw;
}
#body {
  display: block;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  font-family: futura;
  padding: 0 1em 1em 1em;
  a {
    font-weight: bold;
    color: #404040;

    &.router-link-exact-active {
      color: #fa2ac6;
    }
  }
}

#header {
    background-color: #FABC2A;
    height: 10vh;
    width: 100%;
    max-width: 100vw;
    position: top;
    top: 0;
    z-index: 1000;
    box-shadow: 0em 0.1em 1em rgba(0, 0, 0, .4);
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
    font-size: 100%;
    transition: 2s;
    margin-bottom: 10vh;
}
h1 {
    font-family: futura;
    margin: 0;
    font-weight: bold;
    line-height: 100%;
    color: #404040;
    padding: 0 .4em .4em 1em;
}
h4 {
    padding: 0%;
    margin: 0%;
}
img {
    height: 5vh;
    padding-right: 1%;
}
</style>
