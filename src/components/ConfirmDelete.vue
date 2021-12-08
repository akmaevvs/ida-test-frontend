<template>
  <div v-if="show" class="modal-inner">
    <div class="confirm-delete">
      <button
        class="confirm-delete__button confirm-delete__button--confirm"
        @click="Confirm"
      >
        Удалить &#10004;
      </button>
      <button
        class="confirm-delete__button confirm-delete__button--close"
        @click="Close"
      >
        Отмена &#10008;
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "confirm-delete",
  props: {
    show: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    Close() {
      this.$emit("close-event");
    },
    Confirm() {
      this.$emit("confirm-event");
    },
  },
};
</script>

<style lang="scss" scoped>
.modal-inner {
  display: flex;
  justify-content: center;
  align-items: center;

  position: absolute;
  width: 100%;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background-color: #000000a4;
  cursor: default;
  border-radius: 5px;

  .confirm-delete {
    display: flex;
    gap: 10px;
    justify-content: center;
    align-items: center;
    &__button {
      font-size: 18px;
      color: #fff;
      // width: 30px;
      // height: 30px;
      padding: 10px 20px;
      border-radius: 5px;
      box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.603);
      cursor: pointer;
      transition: transform .2s ease-in-out;

      &:hover {
        transform: scale(1.02);
      }

      &--close {
        background-color: #ff8484;
      }
      &--confirm {
        background-color: #7bae73;
      }
    }
  }
}
</style>
