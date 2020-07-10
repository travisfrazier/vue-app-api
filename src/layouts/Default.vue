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

<style lang="scss" scoped>

</style>