<template>
  <nav id="nav" class="navbar navbar-expand-lg navbar-dark bg-danger">
    <div class="container">
      <router-link to="/" class="navbar-brand">{{ stitle }}</router-link>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item ">
            <router-link to="/" class="nav-link active">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/about" class="nav-link active">About</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      stitle: "Vue Js",
    };
  },
};
</script>

<style scoped></style>
