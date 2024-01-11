<template>
  <form @submit.prevent>
    <h4>Create Post</h4>

    <my-input v-model:value="post.title" type="text" placeholder="Title" />
    <my-input v-model:value="post.body" type="text" placeholder="Description" />

    <my-button
      class="btn"
      @click="createPost"
      style="align-self: flex-end; margin-top: 15px"
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
      this.post.id = Date.now();
      this.$emit("create", this.post, "second param", "3 param");
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>

<style scoped>
.btn {
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
  cursor: pointer;
}

form {
  display: flex;
  flex-direction: column;
}
</style>
