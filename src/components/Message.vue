<template>
  <h1>Message Component - {{ message }}</h1></template
>

<script>
export default {
  props: {
    message: {
      type: String,
      required: true,
    },
  },
}
</script>

<style></style>
