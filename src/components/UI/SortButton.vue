<template>
  <button @click="ToogleShowSortStateList" class="sort-button">
    <slot></slot>
    <span class="sort-button__arrow"></span>

    <transition name="fade">
      <div v-if="showSortStateList" class="sort-button__sort-list">
        <button
          @click="SelectSortState(sortState)"
          class="sort-button__sort-state"
          v-for="(sortState, index) in sortStateList"
          :key="index"
        >
          {{ sortState.titleState }}
        </button>
      </div>
    </transition>
  </button>
</template>

<script>
export default {
  name: "sort-button",
  data() {
    return {
      sortStateList: [
        {
          id: "default",
          titleState: "По умолчанию",
        },
        {
          id: "by-name",
          titleState: "По наименованию",
        },
        {
          id: "max-price",
          titleState: "По цене (max)",
        },
        {
          id: "min-price",
          titleState: "По цене (min)",
        },
      ],
      showSortStateList: false,
    };
  },
  methods: {
    ToogleShowSortStateList() {
      this.showSortStateList = !this.showSortStateList;
    },
    SelectSortState(state) {
      this.$emit("select-sort-state-event", state);
    },
  },
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

  &__sort-list {
    position: absolute;
    display: flex;
    flex-direction: column;
    top: 40px;
    z-index: 2;
    background-color: #fffefb;
    box-shadow: 0px 2px 5px #0000001a;
    border-radius: 4px;
    width: max-content;
  }

  &__sort-state {
    cursor: pointer;
    border-bottom: 1px solid #e5e3e3;
    padding: 10px 16px;
    transition: background-color 0.2s ease-in-out;
    // color: var(--default-button-text-color);

    &:first-child {
      border-radius: 4px 4px 0px 0px;
    }

    &:last-child {
      border-radius: 0px 0px 4px 4px;
      border-bottom: none;
    }

    &:hover {
      background-color: #0000001a;
    }
  }
}
</style>
