<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>User name: {{ username }}</p>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
    username: String,
  },
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
