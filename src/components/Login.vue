<template>
  <div>
    <h1 class="text-center mb-5">Login Page</h1>
    <div class="container">
      <div class="row">
        <div class="col-md-6 offset-md-3">
          <form @submit.prevent="handleSubmit">
            <div class="form-group">
              <label for="id">Username or email</label>
              <input
                class="form-control"
                type="text"
                id="id"
                name="id"
                v-model="id"
                placeholder="Enter username or email"
              />
            </div>
            <div class="form-group">
              <label for="pass">Password</label>
              <input
                class="form-control"
                type="password"
                id="password"
                name="password"
                v-model="pass"
                placeholder="Enter password"
              />
            </div>
            <button type="submit" class="btn btn-primary">Login</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "login",
  data: function() {
    return {
      id: "",
      pass: ""
    };
  },
  props: ["identifier", "password"],
  methods: {
    handleSubmit: function() {
      let type = "";
      if (this.id.indexOf("@") > -1) {
        type = "email";
      } else {
        type = "username";
      }
      if (type === "username") {
        if (
          this.id === this.identifier.split("@")[0] &&
          this.pass === this.password
        ) {
          this.$emit("login");
          return this.$router.push("products");
        } else {
          alert(
            `Hint:\nUsername: ${this.identifier.split("@")[0]}\nPassword: ${
              this.password
            }`
          );
          this.id = "";
          this.pass = "";
          return false;
        }
      } else {
        if (this.id === this.identifier && this.pass === this.password) {
          return this.$router.push("products");
        } else {
          alert(`Hint:\nEmail: ${this.identifier}\nPassword: ${this.password}`);
          this.id = "";
          this.pass = "";
          return false;
        }
      }
    }
  }
};
</script>
