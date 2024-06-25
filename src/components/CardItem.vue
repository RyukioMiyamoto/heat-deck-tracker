<template>
  <div class="card">
    {{ value }}
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: [String, Number],
      required: true
    }
  }
}
</script>

<style scoped>
.card {
  width: 100px;
  height: 150px;
  border: 1px solid #ccc;
  margin: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 1.5em;
}
</style>
