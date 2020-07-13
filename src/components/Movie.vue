<template>
  <div class="c-movie">
    <img class="c-movie-image" :src="posterImage" :alt="movie.title" />
    <button v-on:click="addMovieClicked" class="c-movie-button">Add</button>
    <button v-on:click="removeMovieClicked" class="c-movie-button-remove">
      Remove
    </button>
  </div>
</template>

<script>
const POSTER_PATH = 'http://image.tmdb.org/t/p/w154';

export default {
  name: 'Movie',
  props: ['movie'],
  methods: {
    addMovieClicked() {
      this.$emit('addMovie', this.movie);
    },
  },
  computed: {
    posterImage() {
      return `${POSTER_PATH}/${this.movie.poster_path}`;
    },
  },
};
</script>

<style lang="scss">
.c-movie {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.c-movie-image {
  align-self: center;
  margin-bottom: 1rem;
  box-shadow: 0 0 35px black;
}

.c-movie-button {
  width: 8rem;
  margin-bottom: 2rem;
  text-align: center;
  background: green;
  border: none;
  font-size: 0.85rem;
  color: white;
  border-radius: 40px;
  padding: 0.5rem 1rem;
  font-family: 'Courier New', Courier, monospace;
  font-weight: bold;
}

.c-movie-button-remove {
  display: none;
  width: 8rem;
  margin-bottom: 2rem;
  text-align: center;
  background: firebrick;
  border: none;
  font-size: 0.85rem;
  color: white;
  border-radius: 40px;
  padding: 0.5rem 1rem;
  font-family: 'Courier New', Courier, monospace;
  font-weight: bold;
}

.watch-list-movie {
  .c-movie-button {
    display: none;
  }
  .c-movie-button-remove {
    display: block;
  }
}
</style>
