<template>
  <button class="sort-button">
    <slot></slot>
    <span class="sort-button__arrow"></span>
  </button>
</template>

<script>
export default {
  name: "sort-button"
};
</script>

<style lang="scss" scoped>
.sort-button {
  background: #fffefb;
  box-shadow: 0px 2px 5px #0000001a;
  border-radius: 4px;
  padding: 10px 16px;
  cursor: pointer;
  display: flex;
  box-sizing: border-box;
  justify-content: center;
  align-items: center;
  color: var(--default-button-text-color);
  font-size: var(--font-size-button-input);

  &__arrow {
    display: flex;
    justify-content: flex-end;
    position: relative;
    box-sizing: border-box;
    width: 12px;
    &::before {
      content: "";
      display: block;
      width: 5.59px;
      height: 5.59px;
      transform: rotate(45deg);
      border-right: 1.5px solid;
      border-bottom: 1.5px solid;
      box-sizing: border-box;
    }
  }
}
</style>