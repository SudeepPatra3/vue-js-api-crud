<template>
  <div class="post-details text-center">
    <div class="card m-3">
      <div class="card-body">
        <h5>{{ post.title }}</h5>
        <h6>{{ post.body }}</h6>
      </div>
    </div>
    <PostComments />
  </div>
</template>
<script>
import axios from "axios";
import PostComments from "@/views/PostComments.vue";
export default {
  name: "PostDetails",
  components: { PostComments },
  data() {
    return {
      id: this.$route.params.id,
      post: [],
    };
  },
  created() {
    axios
      .get(`https://jsonplaceholder.typicode.com/posts/${this.id}`)
      .then((res) => {
        this.post = res.data;
        console.log(res);
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>
