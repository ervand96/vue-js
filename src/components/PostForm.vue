<template>
  <form @submit.prevent>
    <h4>Crete Posts</h4>
    <my-input v-focus v-model="post.title" type="text" placeholder="Name Posts" />
    <my-input  v-model="post.body" type="text" placeholder="Description" />
    <my-button
      style="align-self: flex-end; margin-top: 15px"
      @click="createPost"
      @click.stop
      >Create</my-button
    >
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      if (this.post.title.trim() && this.post.body.trim() !== "") {
        this.post.id = Date.now();
        this.$emit("create", this.post);
        this.post = {
          title: "",
          body: "",
        };
        this.post.title = "";
        this.post.body = "";
      }
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>
