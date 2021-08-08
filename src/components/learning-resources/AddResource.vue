<template>
  <base-dialog
    v-if="!isSubmittable"
    title="Invalid Input"
    @close-dialog="confirmError"
  >
    <!-- <template #header>
      <h2>Form Error</h2>
    </template> -->

    <template #default>
      <p>At least, one input field is invalid</p>
      <p>Kindly check your inputs to ensure all are filled accurately</p>
    </template>

    <template #actions>
      <base-button @click="confirmError()">Okay</base-button>
    </template>
  </base-dialog>

  <base-card>
    <form @submit.prevent="addResource">
      <div class="form-control">
        <label for="title">Title</label>
        <input v-model="title" type="text" id="title" name="title" />
      </div>

      <div class="form-control">
        <label for="author">Author</label>
        <input v-model="author" type="text" id="author" name="author" />
      </div>

      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          v-model="description"
          name="description"
          id="description"
          cols="30"
          rows="3"
        ></textarea>
      </div>

      <div class="form-control">
        <label for="link">Link</label>
        <input v-model="url" type="url" name="link" id="link" />
      </div>

      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
export default {
  components: { BaseButton },
  inject: ['addSubmittedResource' /* 'isSubmittable' */],
  data() {
    return {
      title: '',
      author: '',
      description: '',
      url: '',
      isSubmittable: true
    };
  },
  methods: {
    addResource() {
      // component is a dynamic component on its parent, hence custom emit won't work but provide from the parent and inject here will rescue us
      if (
        this.title.trim() === '' ||
        this.author.trim() === '' ||
        this.description.trim() === '' ||
        this.url.trim() === ''
      ) {
        this.isSubmittable = false;
        return;
      }

      this.addSubmittedResource(
        this.title,
        this.author,
        this.description,
        this.url
      );

      this.author = '';
      this.title = '';
      this.description = '';
      this.url = '';
    },
    confirmError() {
      this.isSubmittable = true;
    }
  }
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
