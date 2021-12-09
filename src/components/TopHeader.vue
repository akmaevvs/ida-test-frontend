<template>
  <div class="top-header">
    <h3 class="top-header__title">Добавление товара</h3>
    <sort-button @select-sort-state-event="SelectSortState">
      {{ sortState.titleState }}
    </sort-button>
  </div>
</template>

<script>
import SortButton from "@/components/UI/SortButton.vue";
export default {
  name: "top-header",
  components: {
    SortButton,
  },
  data() {
    return {
      sortState: {
        id: "default",
        titleState: "По умолчанию",
      },
    };
  },
  methods: {
    SelectSortState(state) {
      this.sortState = state;
      this.$emit("select-sort-state-event", state);
    },
  },
};
</script>

<style lang="scss" scoped>
.top-header {
  display: flex;
  position: relative;
  width: 100%;
  justify-content: space-between;
  // position: relative;
  z-index: 2;
  background-color: #fefdfa;
  padding: 32px;

  &__title {
    font-size: 28px;
    line-height: 35px;
  }
}
@media screen and (max-width: 600px) {
  .top-header {
    position: sticky;
    top: 0;
    padding: 16px;
    box-shadow: 0px 2px 5px #0000001a;
    &__title {
      font-size: 20px;
      line-height: 35px;
    }
  }
}
</style>
