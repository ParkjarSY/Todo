<template>
  <div id="app">
    <transition>
      <router-view />
    </transition>
  </div>
</template>

<script>
export default {
  name: 'App',
}
</script>

<style>
  @import url('./assets/index.css');
*{
  margin: 0;
  padding:0;

}
  a{
    text-decoration: none;
  }
  ul,ol{
    list-style: none;
  }
  h1,h2,h3,h4,h5{
    font: inherit;
  }
  input,select,button{
    font: inherit;
  }
  html,body{
    height: 100%;
    -webkit-user-select: none;
    -webkit-touch-callout: none;
    -webkit-tap-highlight-color: transparent;
  }
  body{
    font-family:'Segoe UI', Roboto, Oxygen,Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif ;
  }
  #app{
    height: 100%;
    overflow: hidden;
  }
</style>
