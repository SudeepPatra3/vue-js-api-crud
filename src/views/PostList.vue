<template>
  <div class="post-list">
    <div
      class="card mb-3 text-center"
      v-for="post of posts"
      :key="post.id"
      @click="$emit('del-post', post.id)"
    >
      <div class="card-body">
        <h5>
          <router-link :to="`/post-details/${post.id}`">{{
            post.title
          }}</router-link>
        </h5>
        <hr />
        <h6>{{ post.body }}</h6>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "PostList",
  props: ["posts"],
};
</script>
<style scoped>
a {
  color: brown;
  text-decoration: none;
}
</style>
