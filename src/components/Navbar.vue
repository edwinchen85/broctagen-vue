<template>
  <div class="row">
    <div class="col-12">
      <nav class="navbar navbar-expand-lg navbar-light">
        <h1>{{ title }}</h1>
        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav ml-auto">
            <li class="nav-item" :class="{ active: this.$route.path === '/products' }">
              <router-link class="nav-link" to="/products">Products</router-link>
            </li>
            <li class="nav-item" :class="{ active: this.$route.path === '/account' }">
              <router-link class="nav-link" to="/account">Account</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/">Logout</router-link>
            </li>
          </ul>
        </div>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  name: "navbar",
  props: ["title"]
};
</script>

<style scoped>
.navbar {
  padding-right: 0 !important;
}
</style>
