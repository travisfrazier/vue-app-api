<template>
  <div id="movieApp">
    <Header :title='title' />
    <MoviesList />
  </div>
</template>

<script>
import Header from '~/components/Header.vue';
import MoviesList from '~/components/MoviesList.vue';
import Search from '~/components/Search.vue';



export default {
  data() {
    return {
      title: 'Movie Watch List'
    }
  },
  components: {
    Header,
    MoviesList 
  },
  methods: {
   
  }
};
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700&family=Modak&display=swap');

  body {
    margin: 0;
    padding: 0;
    background: #222;
    font-family:'Lato', sans-serif;
  }
  button {
    &:hover {
      cursor: pointer;
      color: black;
    }
  }

  h1, h2, h3, h4, h5 {
    font-family: 'Modak', cursive;
    font-weight: 400;
  }
</style>