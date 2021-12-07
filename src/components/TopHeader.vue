<template>
  <div class="top-header">
    <h3 class="top-header__title">Добавление товара</h3>
    <sort-button>
      По умолчанию
    </sort-button>
  </div>
</template>

<script>
import SortButton from "@/components/UI/SortButton.vue";
export default {
  name: "top-header",
  components: {
    SortButton
  }
};
</script>

<style lang="scss" scoped>
.top-header {
  display: flex;
  width: 100%;
  justify-content: space-between;
  position: relative;


  &__title {
      font-size: 28px;
      line-height: 35px;
  }
}
</style>