<template>
  <div id="app">
    <Header/>
    <Main/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main,
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;900&display=swap');

  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    font-size: 100%;
    font-family: 'Roboto', sans-serif;
  }
  body {
    background-color: #434343;
  }
</style>
