<template>
  <div>
    <navbar :title="title"></navbar>
    <product-list :products="products"></product-list>
  </div>
</template>
<script>
import Navbar from "./Navbar.vue";
import ProductList from "./ProductList.vue";

export default {
  name: "products",
  data: function() {
    return {
      title: "Products"
    };
  },
  props: ["products"],
  components: {
    Navbar,
    ProductList
  }
};
</script>
