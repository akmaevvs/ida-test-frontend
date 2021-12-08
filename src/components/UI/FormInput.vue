<template>
  <input
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
    class="form-input"
    type="text"
    :placeholder="placeholder"
  />
</template>

<script>
export default {
  name: "form-input",
  props: {
    placeholder: {
      type: String,
      default: "Введите свое значение",
    },
    modelValue: {
      type: String,
      default: "",
    },
  },
  emits: ["update:modelValue"],
};
</script>

<style lang="scss" scoped>
.form-input {
  background: #fffefb;
  box-shadow: 0px 2px 5px #0000001a;
  border-radius: 4px;
  padding: 10px 16px;

  font-style: normal;
  font-weight: normal;
  font-size: 12px;
  line-height: 15px;

  width: 100%;

  
}
</style>
