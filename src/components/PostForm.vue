<template>
  <form @submit.prevent>
    <h4>Create Post</h4>
    <!-- <input
        v-bind:value="title"
        @input="inputTitle"
        class="input"
        type="text"
        placeholder="Title"
      /> -->
    <!-- <input
      :value="post.title"
      @input="post.title = $event.target.value"
      class="input"
      type="text"
      placeholder="Title"
    /> -->
    <input v-model="post.title" class="input" type="text" placeholder="Title" />
    <input
      v-model="post.body"
      class="input"
      type="text"
      placeholder="Description"
    />
    <button class="btn" @click="createPost">Create</button>
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
.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}

.btn {
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
  cursor: pointer;
}
</style>
