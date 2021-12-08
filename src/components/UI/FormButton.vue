<template>
  <button type="submit" :class="{ 'form-button__valid': valid }" class="form-button">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "form-button",
  props: {
    valid: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style lang="scss" scoped>
.form-button {
  width: 100%;
  box-sizing: border-box;
  padding: 10px;
  background-color: #eeeeee;
  border-radius: 10px;
  cursor: default;
  transition: background-color .2s ease-in-out;

  &__valid {
    background-color: #7BAE73;
    cursor: pointer;
    color: #fff;
  }
}
</style>
