<template>
  <div>
    <div
      class="row d-flex mb-3 align-items-center"
      v-for="(item, index) in products"
      :key="item.id"
      :data-index="index"
    >
      <div class="col-8 offset-2 col-sm-4 offset-sm-0">
        <img class="img-fluid d-block" :src="item.image" :alt="item.name" />
      </div>
      <div class="col-sm-8">
        <h3 class="text-info">{{ item.name }}</h3>
        <p class="mb-0">{{ item.description }}</p>
        <div class="h5 float-right mt-4">
          <price :value="Number(item.price)"></price>
          <span>Quantity: {{ item.quantity }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Price from "./Price.vue";

export default {
  name: "product-list",
  components: { Price },
  props: ["products"]
};
</script>
