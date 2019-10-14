<template>
  <span
    class="mr-4"
  >Price: {{ this.prefix + Number.parseFloat(this.value).toFixed(this.precision) }}</span>
</template>

<script>
export default {
  props: {
    value: Number,
    prefix: {
      type: String,
      default: "$"
    },
    precision: {
      type: Number,
      default: 2
    }
  }
};
</script>
