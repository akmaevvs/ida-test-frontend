<template>
  <input
    :value="modelValue"
    @input="EmitInput($event)"
    class="form-input"
    :placeholder="placeholder"
  />
</template>

<script>
export default {
  name: "form-input",
  props: {
    placeholder: {
      type: String,
      default: "Введите свое значение"
    },
    modelValue: {
      type: String,
      default: ""
    }
  },
  emits: ["update:modelValue"],
  methods: {
    EmitInput($event) {
      $event.target.value = $event.target.value.replace(/[^0-9 ]/gm, "");
      this.$emit("update:modelValue", $event.target.value);
    }
  }
};
</script>

<style lang="scss" scoped>
.form-input {
  
}
</style>
