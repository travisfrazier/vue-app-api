<template>
  <div>
    <Search v-on:onChildToParent="onChildClick" />
    <ul class="movie-listing">
      <li class="movie-listing-item" v-for="movie in movies">
        <Movie :movie="movie" />
      </li>
    </ul>
  </div>
</template>

<script>
const axios = require('axios');

export default {
  name: 'MoviesList',
  components: {
    Movie: () => import('./Movie'),
    Search: () => import('./Search')
  },
  data() {
    return {
      movies: [],
      searchQuery: ''
    };
  },
  methods: {
    fetchData: async function() {
      try {
        const response = await axios.get(`https://api.themoviedb.org/3/search/movie?api_key=0af3b5de5a542e42116f3e2e08d52d2a&language=en-US&query=${this.searchQuery}&page=1&include_adult=false`);
        console.log(response.data.results);
        const movies = await response.data;
        this.movies = movies.results;
      } catch (error) {
        console.error(error);
      }
    },
    onChildClick(value) {
      this.searchQuery = value
      this.fetchData();
    }
  }
};
</script>

<style lang="scss" scoped>
.movie-listing .movie-listing-item {
  list-style-type: none;
}

.movie-listing {
  display: grid;
  list-style: none;
  padding: 1rem;
  margin: 0;
  grid-row-gap: 1rem;
  grid-template-columns: repeat(6, 1fr);
}
</style>
