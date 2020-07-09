<template>
  <ul class="movie-listing">
    <li class="movie-listing-item" v-for="movie in movies">
      <Movie :movie="movie" />
    </li>
  </ul>
</template>

<script>
export default {
  name: 'MoviesList',
  components: {
    Movie: () => import('./Movie'),
  },
  data() {
      return {
          movies: []
      }
  },
  created: function() {
      this.fetchData();
  },
  methods: {
    fetchData: async function() {
      try {
        const res = await fetch(
          'https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=3e176f464be990c4b8fefff841cef7b4'
        );
        const movies = await res.json();
        this.movies = movies.results;
      } catch (e) {
        console.log(e);
      }
    },
  },
};
</script>

<style scoped>
.movie-listing .movie-listing-item {
  list-style-type: none;
}

.movie-listing {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}

</style>
