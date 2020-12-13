<template>
  <div class="home">
    <AddPost v-on:add-post="addPost" />
    <PostList :posts="posts" v-on:del-post="deletePost" />
  </div>
</template>

<script>
import axios from "axios";
// @ is an alias to /src
import AddPost from "@/views/AddPost.vue";
import PostList from "@/views/PostList.vue";

export default {
  name: "Home",
  components: { AddPost, PostList },
  data() {
    return {
      posts: [],
      errors: [],
    };
  },
  methods: {
    addPost(newPost) {
      const { title, body } = newPost;
      axios
        .post("https://jsonplaceholder.typicode.com/posts", {
          title,
          body,
        })
        .then((res) => (this.posts = [...this.posts, res.data]))
        .catch((err) => console.log(err));
    },
    deletePost(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/posts/${id}`)
        .then(res => {
          this.posts = this.posts.filter(post => post.id !== id);
          res
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
  created() {
    axios
      .get(`https://jsonplaceholder.typicode.com/posts`)
      .then((res) => {
        this.posts = res.data;
        console.log(res);
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>
<style>
body {
  background: grey;
}
</style>
