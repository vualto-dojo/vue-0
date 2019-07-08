<template>
  <li>{{ label }} : {{ value }}</li>
</template>

<script>
export default {
  name: "Translation",
  props: {
    label: String,
    value: String
  }
};
</script>

<style scoped>
li {
  border: 1px solid #f00;
}
</style>
