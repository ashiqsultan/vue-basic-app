<template>
  <div id="app" class="container m-3">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="A Basic Vue app" username="myName" />
    <MyComponent />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import MyComponent from "./components/MyComponent.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    MyComponent,
  },
};
</script>

<style>
</style>
