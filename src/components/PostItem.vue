<template>
  <div class="posts">
    <div>
      <div>
        <strong>{{ post.id }}</strong>
      </div>
      <div><strong>Title:</strong>{{ post.title }}</div>
      <div><strong>Description:</strong>{{ post.body }}</div>
    </div>
    <div class="post__btn">
      <my-button @click="$router.push(`/posts/${post.id}`)">Open</my-button>
      <my-button @click="$emit('remove', post)">Delete</my-button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      require: true,
    },
  },
};
</script>

<style scoped>
.posts {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 15px;
  padding: 15px;
  border: 2px solid teal;
}

.post__btn {
  display: flex;
  column-gap: 10px;
}
</style>
