<template>
  <ul>
    <resource-item
      v-for="resource in resources"
      :title="resource.title"
      :id="resource.id"
      :description="resource.description"
      :author="resource.author"
      :link="resource.link"
      :key="resource.id"
    ></resource-item>
  </ul>
</template>

<script>
import ResourceItem from './ResourceItem.vue';

export default {
  // props: ['resources'],
  components: {
    ResourceItem
  },
  inject: ['resources']
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
