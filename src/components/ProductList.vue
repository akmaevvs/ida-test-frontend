<template>
  <div class="product-list">
    <transition-group name="list">
      <product-card
        v-for="productCard in productList"
        :key="productCard.id"
        :productCard="productCard"
        @delete-product-event="DeleteProduct"
      />
    </transition-group>
  </div>
</template>

<script>
import ProductCard from "@/components/ProductCard.vue";
export default {
  name: "product-list",
  components: {
    ProductCard,
  },
  props: {
    productList: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    DeleteProduct(id) {
      console.log(id);
      this.$emit("delete-product-event", id);
    },
  },
};
</script>

<style lang="scss" scoped>
.product-list {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  justify-content: flex-end;
  width: 100%;
  position: relative;
}
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease-in-out;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(-100%);
}
</style>
