<template>
  <the-header title="MyResources"></the-header>
  <!-- <stored-resources :resources="storedResources"  ></stored-resources> -->
  <the-resources></the-resources>
</template>

<script>
  // import StoredResources from "./components/learning-resources/StoredResources.vue";
  import TheHeader from "./components/layouts/TheHeader.vue";
  import TheResources from "./components/learning-resources/TheResources.vue"

export default {
  components: {
    // StoredResources,
    TheHeader,
    TheResources,
  },
  data() {
    return {
      
    };
  },
};
</script>

<style>
  body {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
