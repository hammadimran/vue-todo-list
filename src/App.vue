<template>
  <div id="app">


    <my-compo></my-compo>

    <!--<router-view/>-->\

  </div>
</template>

<script>

  import compo from './components/mycomponent'

export default {
  name: 'App',
  components: {

    //'todo-list':mylist,
    'my-compo':compo,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
