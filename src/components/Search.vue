<template>
  <form class="c-search__form" v-on:submit.prevent>
    <input class="c-input" type="text" v-model="childMessage" />
    <button class="c-form__button" v-on:click="searchQuery">Search</button>
  </form>
</template>

<script>
export default {
  name: 'Search',
  data() {
    return {
      childMessage: '',
    };
  },
  methods: {
    searchQuery() {
      this.$emit('onChildToParent', this.childMessage);
    },
  },
};
</script>

<style lang="scss" scoped>
.c-search__form {
  display: flex;
  justify-content: center;
  padding-top: 2rem;
  padding-bottom: 2rem;
}
.c-form__button {
  background: green;
  border: none;
  border-radius: 40px;
  color: white;
  padding: 1rem 2.5rem;
  font-size: 1rem;
  font-family: 'Courier New', Courier, monospace;
  font-weight: bold;
}
.c-input {
  border: none;
  border-radius: 40px;
  font-size: 1rem;
  margin-right: 2rem;
  padding: 1rem;
  font-family: 'Courier New', Courier, monospace;
}
</style>
