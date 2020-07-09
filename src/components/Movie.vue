<template>
  <div>
      <img :src="posterImage" :alt="movie.title" />
  </div>
</template>

<script>
const POSTER_PATH = "http://image.tmdb.org/t/p/w154";

export default {
  name: 'Movie',
  props: ['movie'],
  computed: {
      posterImage() {
          return `${POSTER_PATH}/${this.movie.poster_path}`;
      }
  }
};
</script>

<style lang="scss" scoped></style>
