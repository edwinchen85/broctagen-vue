<template>
  <div id="app" class="container mt-5">
    <router-view
      :identifier="identifier"
      :password="password"
      :isLoggedIn="isLoggedIn"
      :products="products"
      :account="account"
      @login="updateLogin"
      @account="updateAccount"
      @password="updatePassword"
    ></router-view>
  </div>
</template>

<script>
export default {
  name: "app",
  data: function() {
    return {
      identifier: "test@test.com",
      password: "0000",
      isLoggedIn: false,
      products: null,
      account: {
        name: "Edwin Chen",
        birthday: "1985-05-26",
        age: 34,
        education: "Bachelor of Engineering",
        about:
          "I am a self-taught programmer passionate in web development technologies with focus on front-end. During my tenure working as a software developer, I’ve been given great opportunities to gain wide range of experience from participating full software development life cycle to perform DevOps work. While I gain a lot of industry knowledge on my job, I keep myself abreast of other latest evolving technologies. I’ve been praised by my clients as well organized and meticulous coder when looking over my shoulder working. My normal working day requires me to handle multiple tasks simultaneously such as communicating with stakeholders while resolving bug issues and working on new features."
      }
    };
  },
  methods: {
    updateLogin: function() {
      this.isLoggedIn = !this.isLoggedIn;
    },
    updateAccount: function(data) {
      this.account = { ...this.account, ...data };
    },
    updatePassword: function(data) {
      this.password = data;
    }
  },
  mounted: function() {
    fetch("https://hplussport.com/api/products/order/price")
      .then(response => response.json())
      .then(data => {
        this.products = data
          .map(item => {
            item.quantity = Math.floor(Math.random() * 100);
            return item;
          })
          .slice(0, 10);
      });
  }
};
</script>
