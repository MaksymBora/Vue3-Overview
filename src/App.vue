<template>
  <div class="app">
    <h1>Page with Posts</h1>
    <my-button @click="fetchPosts">Receive Posts</my-button>

    <!-- <input type="text" v-model.number="modificatorValue" /> -->
    <my-button @click="showDialog" style="margin: 15px 0"
      >Create Post</my-button
    >

    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost" />
    </my-dialog>

    <post-list :posts="posts" @remove="removePost" />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import axios from "axios";

export default {
  components: {
    PostList,
    PostForm,
  },

  data() {
    return {
      posts: [
        { id: 1, title: "JavaScript", body: "Description of post!" },
        { id: 2, title: "JavaScript 2", body: "Description of post 2!" },
        { id: 3, title: "JavaScript 3", body: "Description of post 3!" },
        { id: 4, title: "JavaScript 3", body: "Description of post 3!" },
      ],
      dialogVisible: false,
      modificatorValue: "",
    };
  },
  methods: {
    // inputTitle(event) {
    //   this.title = event.target.value;
    // },
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/posts?_limit=10"
        );
        console.log(response);
      } catch (e) {
        console.log(e);
      }
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}
</style>
