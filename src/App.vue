<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
body {
    background: url('./assets/avocados.jpg');
    background-size: contain;
}
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}
button {
    border-style: solid;
    border-width: 0px;
    cursor: pointer;
    font-weight: normal;
    line-height: normal;
    margin: 0 0 1.25rem;
    position: relative;
    text-decoration: none;
    text-align: center;
    -webkit-appearance: none;
    -webkit-border-radius: 0;
    border-radius: 0;
    display: inline-block;
    padding-top: .5rem;
    padding-right: 1rem;
    padding-bottom: .5rem;
    padding-left: 1rem;
    font-size: 1rem;
    background-color: #6C8F32;
    color: #FFFFFF;
    -webkit-transition: background-color 300ms ease-out;
    transition: background-color 300ms ease-out;
    border: 1px solid #356211;
    border-bottom: 5px solid #356211;
    margin-top: 25px;
}
h1 {
    color: #efefef;
}
label {
    display: inline-block;
    margin: 20px 0 10px
}
i {
    margin-right: 4px;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
