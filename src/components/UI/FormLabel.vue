<template>
  <label class="form-label" for>
    <slot></slot>
    <div v-if="required" class="red-dot"></div>
  </label>
</template>

<script>
export default {
  name: "form-label",
  props: {
    required: {
      type: Boolean,
      default: false
    }
  }
};
</script>

<style lang="scss" scoped>
.form-label {
  font-family: Source Sans Pro;
  font-style: normal;
  font-weight: normal;
  font-size: 10px;
  line-height: 13px;
  letter-spacing: -0.02em;
  position: relative;
  width: max-content;

  & .red-dot {
    display: block;
    width: 4px;
    height: 4px;
    border-radius: 4px;
    background-color: #ff8484;
    position: absolute;
    right: -4px;
    top: 0;
  }
}
</style>