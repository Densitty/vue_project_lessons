<template>
  <base-card @new-resource="addNewResource">
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResourcesMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="selectedTab === 'add-resource' ? null : 'flat'"
      >Add Resources</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
  components: {
    StoredResources,
    AddResource
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      isSubmittable: true,
      storedResources: [
        {
          id: '001',
          title: 'JavaScript OOP - Advanced Concepts',
          author: 'Mosh Hammedani',
          description:
            'The Detailed Resource for Object Oriented Learning in JS',
          link: 'https://udemy.com'
        },
        {
          id: '002',
          title: 'Mastering SEO - The Complete Guide',
          author: 'Kelly Dexter',
          description:
            'The art and science of making your online presence seen everywhere.',
          link: 'https://udemy.com'
        }
      ]
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      isSubmittable: this.isSubmittable,
      addSubmittedResource: this.addNewResource,
      deleteResource: this.removeResource
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addNewResource(title, author, desc, link) {
      this.storedResources.unshift({
        id: new Date().getTime().toString(),
        title,
        author,
        description: desc,
        link
      });
      // set the selectedTab to default value to change view to that component
      this.selectedTab = 'stored-resources';
    },
    removeResource(id) {
      const resIndex = this.storedResources.findIndex(res => res.id === id);
      this.storedResources.splice(resIndex, 1);
    }
  },
  computed: {
    storedResourcesMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    }
  }
};
</script>
