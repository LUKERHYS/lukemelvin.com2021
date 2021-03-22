<template>
<div>
    <div>
      <div id="header">
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
    display: block;
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
    transition: 2s;
    margin-bottom: 10vh;

    h1 {
      font-family: futura;
      color: #404040;
      font-weight: bold;
      line-height: 100%;
      margin: 0;
      padding: 0 .4em .4em 1em;
  }
}

#nav {
  font-family: futura;
  padding: 0 1em 1em 1em;
  a {
    font-weight: bold;
    color: #404040;
    text-decoration-line: none;

    &.router-link-exact-active {
      color: #fa2ac6;
    }
  }
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
