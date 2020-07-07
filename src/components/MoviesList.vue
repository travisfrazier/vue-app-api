<template>
  <div>
    {{ movie.title }}
  </div>
</template>

<script>
export default {
  name: 'MoviesList',
  data() {
      return {
          movie: {}
      }
  },
  created: function() {
      this.fetchData();
  },
  methods: {
    fetchData: async function() {
      try {
        const res = await fetch(
          'https://api.themoviedb.org/3/movie/550?api_key=3e176f464be990c4b8fefff841cef7b4'
        );
        this.movie = await res.json();
        return movie;
      } catch (e) {
        console.log(e);
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
