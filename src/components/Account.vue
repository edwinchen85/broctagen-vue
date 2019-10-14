<template>
  <div>
    <navbar :title="title"></navbar>
    <div class="container">
      <div class="row">
        <div class="col-md-6 offset-md-3">
          <form @submit.prevent="updateAccount">
            <div class="form-group">
              <label for="name">Name</label>
              <input
                class="form-control"
                type="text"
                id="name"
                name="name"
                v-model="name"
                placeholder="Enter your name"
              />
            </div>
            <div class="form-group">
              <label for="pass">Birthday</label>
              <input
                class="form-control"
                type="date"
                id="birthday"
                name="birthday"
                v-model="birthday"
                placeholder="Enter your birthday"
              />
            </div>
            <div class="form-group">
              <label for="age">Age</label>
              <input
                class="form-control"
                type="number"
                id="age"
                name="age"
                v-model="age"
                placeholder="Enter your age"
              />
            </div>
            <div class="form-group">
              <label for="education">Education Level</label>
              <input
                class="form-control"
                type="text"
                id="education"
                name="education"
                v-model="education"
                placeholder="Enter your education level"
              />
            </div>
            <div class="form-group">
              <label for="about">About Me</label>
              <textarea
                class="form-control"
                type="text"
                id="about"
                name="about"
                v-model="about"
                placeholder="Tell us more about yourself..."
              ></textarea>
            </div>
            <button type="submit" class="btn btn-primary">Update</button>
          </form>

          <div v-if="showModal">
            <transition name="modal">
              <div class="modal-mask">
                <div class="modal-wrapper">
                  <div class="modal-dialog" role="document">
                    <div class="modal-content">
                      <div class="modal-header">
                        <h5 class="modal-title">Change Password</h5>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                          <span aria-hidden="true" @click="showModal = false">&times;</span>
                        </button>
                      </div>
                      <div class="modal-body">
                        <p>Modal body text goes here.</p>
                        <div class="form-group">
                          <label for="old_password">Old password</label>
                          <input
                            type="password"
                            class="form-control"
                            id="old_password"
                            name="old_password"
                            v-model="old_password"
                          />
                        </div>
                        <div class="form-group">
                          <label for="new_password">New password</label>
                          <input
                            type="password"
                            class="form-control"
                            id="new_password"
                            name="new_password"
                            v-model="new_password"
                          />
                        </div>
                        <div class="form-group">
                          <label for="confirm_password">Confirm password</label>
                          <input
                            type="password"
                            class="form-control"
                            id="confirm_password"
                            name="confirm_password"
                            v-model="confirm_password"
                          />
                        </div>
                      </div>
                      <div class="modal-footer">
                        <button
                          type="button"
                          class="btn btn-secondary"
                          @click="showModal = false"
                        >Close</button>
                        <button
                          type="submit"
                          class="btn btn-primary"
                          @click="updatePassword"
                        >Save changes</button>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </transition>
          </div>
          <button class="btn btn-success mt-4" @click="showModal = true">Change Password</button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Navbar from "./Navbar.vue";

export default {
  name: "login",
  data: function() {
    return {
      title: "Your Account",
      name: this.account.name,
      birthday: this.account.birthday,
      age: this.account.age,
      education: this.account.education,
      about: this.account.about,
      showModal: false,
      old_password: "",
      new_password: "",
      confirm_password: ""
    };
  },
  props: ["account", "password"],
  components: { Navbar },
  methods: {
    updateAccount: function() {
      this.$emit("account", {
        name: this.name,
        birthday: this.birthday,
        age: this.age,
        education: this.education,
        about: this.about
      });
      alert("Your account has been updated!");
    },
    updatePassword: function() {
      if (
        this.old_password === "" ||
        this.new_password === "" ||
        this.confirm_password === ""
      ) {
        alert("Please fill all the password fields. Thank you.");
      } else if (this.old_password !== this.password) {
        alert("You have entered wrong old password. Please try again.");
      } else if (this.new_password !== this.confirm_password) {
        alert(
          "Your new password and confirm password don't match. Please try again."
        );
      } else {
        this.$emit("password", this.new_password);
        alert("Your password has been updated!");
        this.showModal = false;
      }
    }
  }
};
</script>

<style scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}
textarea {
  min-height: 280px;
}
</style>
