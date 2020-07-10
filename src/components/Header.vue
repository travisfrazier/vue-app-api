<template>
    <header class="c-header">
        <h1>{{ title }}</h1>
    </header>
</template>

<script>
    export default {
        name: 'Header',
        props: {
            title: String
        }
    }
</script>

<style lang="scss" scoped>
header {
  background-color: #111;
  padding: 20px;
  color: white;
}
h1 {
  margin: 0 auto;
  text-transform: uppercase;
  text-align: center;
  font-family:'Courier New', Courier, monospace;
}
</style>