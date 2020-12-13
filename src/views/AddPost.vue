<template>
  <div class="add-posts">
    <div class="mb-3 mt-3">
      <div class="row  text-center">
        <div class="col text-right mb-3">
          <button class="btn btn-primary" @click="formShow">
            Create New Post
          </button>
        </div>
      </div>
      <div class="card mb-3" v-if="formDiv">
        <div class="card-body">
          <form method="post" @submit.prevent="addPost">
            <div class="form-group">
              <label>Post Title</label>
              <input
                v-model="title"
                type="text"
                placeholder="Enter Post Title"
                name="title"
                class="form-control"
              />
            </div>
            <div class="form-group">
              <label>Post Detail</label>
              <input
                v-model="body"
                type="text"
                placeholder="Enter Post Detail"
                name="body"
                class="form-control"
              />
            </div>
            <div class="row">
              <div class="col-6 mx-auto m-3">
                <button class="btn btn-success btn-block">Create</button>
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "AddPost",
  data() {
    return {
      formDiv: false,
      title: "",
      body: "",
    };
  },
  methods: {
    formShow() {
      this.formDiv = true;
    },
    addPost() {
      const newPost = {
        title: this.title,
        body: this.body,
      };
      // send data to parent
      this.$emit("add-post", newPost);
      (this.title = ""), (this.body = "");
    },
  },
};
</script>
