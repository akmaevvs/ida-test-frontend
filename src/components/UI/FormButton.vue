<template>
  <button class="form-button">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "form-button"
};
</script>

<style lang="scss" scoped>
.form-button {
  width: 100%;
  box-sizing: border-box;
  padding: 10px;
  background: #eeeeee;
  border-radius: 10px;
  cursor: pointer;
}
</style>