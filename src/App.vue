<!-- <template>
  <div>Hello!</div>
  <div>
    <div>
      <button @click="addLike">Like</button>
      <button @click="addDisLike">Dislike</button>
    </div>
    Q-ty likes: <strong>{{ likes }}</strong> Q-ty dis-likes:
    <strong>{{ dislikes }}</strong>
  </div>
</template>

<script>
export default {
  data() {
    return {
      likes: 0,
      dislikes: 0,
    };
  },
  methods: {
    addLike() {
      this.likes += 1;
    },
    addDisLike() {
      this.dislikes += 1;
    },
  },
};
</script>

<style></style> -->

<template>
  <div class="app">
    <post-form @create="createPost" />
    <post-list :posts="posts" @remove="removePost" />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";

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
    };
  },
  methods: {
    // inputTitle(event) {
    //   this.title = event.target.value;
    // },
    createPost(post) {
      this.posts.push(post);
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
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
