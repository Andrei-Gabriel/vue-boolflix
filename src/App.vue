<template>
  <div id="app">
    <Header @ricerca="ricercaaa"/>
    <Main :serie="series" :film="films"/>
  </div>
</template>

<script>
  import axios from 'axios';
  import Header from './components/Header.vue'
  import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },

  data() {
    return {
      films: [],
      series: [],
    }
  },

  methods: {
    ricercaaa(payload) {
      // Film
      axios.get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: '34d2bf6e1a79c2b489bb5e9909932946',
          language: 'it-IT',
          query: payload,
        }
      })
      .then((response) => {
        this.films = response.data.results;
      })
      .catch((error) => {
        console.log(error); 
      });

      // Serie TV
      axios.get("https://api.themoviedb.org/3/search/tv", {
        params: {
          api_key: '34d2bf6e1a79c2b489bb5e9909932946',
          language: 'it-IT',
          query: payload,
        }
      })
      .then((response) => {
        this.series = response.data.results;
      })
      .catch((error) => {
        console.log(error); 
      });
    }
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
