<template>
  <main>
    <Search v-on:onChildToParent="onChildClick" />
    <div class="movie-listing-container">
      <div class="movie-result-container">
        <ul class="movie-listing">
          <li class="movie-listing-item" v-for="movie in movies.slice(0, 1)">
            <Movie class="result-movie" v-on:addMovie="addToList" :movie="movie" />
          </li>
        </ul>
      </div>
      <div class="watch-list-container">
        <h2 class="movie-listing__heading">Gotta See These</h2>
        <ul class="movie-listing watch-list">
          <li class="movie-listing-item" v-for="movie in watchList">
            <Movie
              v-on:removeMovie="removeFromList"
              class="watch-list-movie"
              :movie="movie"
            />
          </li>
        </ul>
      </div>
    </div>
  </main>
</template>

<script>
const axios = require('axios');

export default {
  name: 'MoviesList',
  components: {
    Movie: () => import('./Movie'),
    Search: () => import('./Search'),
  },
  data() {
    return {
      movies: [],
      searchQuery: '',
      watchList: [],
    };
  },
  methods: {
    fetchData: async function() {
      try {
        const response = await axios.get(
          `https://api.themoviedb.org/3/search/movie?api_key=3e176f464be990c4b8fefff841cef7b4&language=en-US&query=${
            this.searchQuery
          }&page=1&include_adult=false`
        );
        const movies = await response.data;
        console.log(movies.results);
        this.movies = movies.results;
      } catch (error) {
        console.error(error);
      }
    },
    onChildClick(value) {
      this.searchQuery = value;
      this.fetchData();
    },
    addToList(movie) {
      this.watchList.push(movie);
    },
    removeFromList(movie) {
      const index = this.watchList.indexOf(movie);
      this.watchList.splice(index, 1);
    },
  },
};
</script>

<style lang="scss">
.movie-listing-container {
  padding-top: 2rem;
  display: grid;
  grid-template-columns: 30% 1fr;
  @media only screen and (max-width: 850px) {
    grid-template-columns: 1fr;
  }
}

.movie-listing .movie-listing-item {
  list-style-type: none;
}

.result-movie {
  .c-movie-image {
    width: 11rem;
  }
}

.watch-list-movie {
  .c-movie-image {
    width: 8rem;
  }
}

.movie-listing {
  display: grid;
  list-style: none;
  padding: 1rem;
  margin: 0;
  grid-row-gap: 1rem;
}
.movie-listing__heading {
  color: white;
  text-align: center;
}

.watch-list {
  grid-template-columns: repeat(4, 1fr);
  @media only screen and (max-width: 600px) {
      grid-template-columns: repeat(3, 1fr);
  }
  @media only screen and (max-width: 450px) {
      grid-template-columns: repeat(2, 1fr);
  }
}

h2 {
  font-size: 2rem;
}
</style>
