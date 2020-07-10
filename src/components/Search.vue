<template>
  <form class="c-search__form" v-on:submit.prevent>
    <input class="form-search" type="text" v-model="childMessage" />
    <button v-on:click="searchQuery">Search</button>
  </form>
</template>

<script>
export default {
  name: 'Search',
  data() {
    return {
      childMessage: ''
    };
  },
  methods: {
      searchQuery() {
          this.$emit('onChildToParent', this.childMessage)
      }
  }
};
</script>

<style lang="scss" scoped>
.c-search__form {
  display: flex;
  justify-content: center;
}
</style>
