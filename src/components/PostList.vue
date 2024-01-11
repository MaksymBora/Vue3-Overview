<template>
  <div v-if="posts.length > 0">
    <h3>List of Users</h3>
    <post-item
      v-for="post in posts"
      :post="post"
      :key="post.id"
      @remove="$emit('remove', post)"
    />
  </div>
  <h2 v-else style="color: red">List of Users is empty!</h2>
</template>

<script>
import PostItem from "@/components/PostItem";

export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
  components: { PostItem },
};
</script>

<style scoped></style>
