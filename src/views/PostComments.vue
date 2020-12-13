<template>
  <div class="post-comments">
    <h5 class="text-warning text-center">Post Comments</h5>
    <div class="card">
      <div
        class="card mb-3 text-center"
        v-for="comment in comments"
        :key="comment.id"
      >
        <div class="card-body">
          <h5>Name - {{ comment.name }}</h5>
          <h6> Email - {{ comment.email }}</h6>
          <h6>Comment - {{ comment.body }}</h6>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "PostComments",
  data() {
    return {
      id: this.$route.params.id,
      comments: [],
    };
  },
  created() {
    axios
      .get(`https://jsonplaceholder.typicode.com/comments?postId=${this.id}`)
      .then((res) => {
        this.comments = res.data;
        console.log(res);
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>
