<template>
  <div class="c-movie">
    <img class="c-movie-image" :src="posterImage" :alt="movie.title" />
    <button class="c-movie-button">Add</button>
  </div>
</template>

<script>
const POSTER_PATH = 'http://image.tmdb.org/t/p/w154';

export default {
  name: 'Movie',
  props: ['movie'],
  computed: {
    posterImage() {
      return `${POSTER_PATH}/${this.movie.poster_path}`;
    },
  },
};
</script>

<style lang="scss" scoped>
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
  width: 6rem;
  margin-bottom: 2rem;
}
</style>
