<template>
  <div v-if="posts.length > 0">
    <h3>List Posts</h3>
    <transition-group name="list">
      <post-item
        v-for="post in posts"
        :post="post"
        :key="post.id"
        @remove="$emit('remove', post)"
      />
    </transition-group>
  </div>
  <div v-else>
    <h2 style="color: darkred">List the post empty</h2>
  </div>
</template>

<script>
import PostItem from "./PostItem.vue";
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.posts {
  margin-top: 15px;
  padding: 15px;
  border: 2px solid teal;
}

.list-item {
  display: inline-block;
  margin-right: 10px;
}

.list-enter-active,
.list-leave-active {
  transition: all 0.4s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(130px);
}

.list-move {
  transition: transform 0.4s ease;
}
</style>
