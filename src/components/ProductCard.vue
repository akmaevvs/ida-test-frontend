<template>
  <div class="product-card">
    <img class="product-card__img" :src="productCard?.img" alt />
    <div class="product-card__info">
      <h4 class="product-card__title">{{ productCard?.title }}</h4>
      <p class="product-card__desc">
        {{ productCard?.desc }}
      </p>
      <p class="product-card__price">{{ productCard?.price }} руб.</p>
    </div>
    <transition name="fade">
      <confirm-delete
        :show="showConfirm"
        @close-event="CloseConfirmModal"
        @confirm-event="DeleteProduct"
      />
    </transition>
    <transition name="fade">
      <button @click="ShowConfirmModal" class="product-card__delete">
        <img
          class="product-card__delete-img"
          :src="deleteButtonImg"
          alt="Logo"
        />
      </button>
    </transition>
  </div>
</template>

<script>
import defaultImgProductCard from "@/assets/img/default_img_product_card.png";
import deleteButtonImg from "@/assets/img/delete_button_img.png";
import ConfirmDelete from "@/components/ConfirmDelete.vue";

export default {
  name: "product-list",
  components: {
    ConfirmDelete,
  },
  data() {
    return {
      defaultImgProductCard,
      deleteButtonImg,
      showConfirm: false,
    };
  },

  props: {
    productCard: {
      type: Object,
      default: () => {
        return {
          id: "0",
          img: defaultImgProductCard,
          title: "Наименование товара",
          desc: `Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк`,
          price: "10 000",
        };
      },
    },
  },
  methods: {
    ShowConfirmModal() {
      this.showConfirm = true;
    },
    CloseConfirmModal() {
      this.showConfirm = false;
    },
    DeleteProduct() {
      this.$emit("delete-product-event", this.productCard.id);
    },
  },
};
</script>

<style lang="scss" scoped>
.product-card {
  display: flex;
  position: relative;
  flex-direction: column;
  width: 100%;
  max-width: 332px;

  background: #fffefb;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;

  cursor: pointer;

  transition: transform 0.2s ease-in-out;

  &:hover {
    transform: scale(1.02);
  }

  &__img {
    width: 100%;
    border-radius: 5px 5px 0px 0px;
  }
  &__info {
    display: flex;
    flex-direction: column;
    gap: 16px;
    padding: 16px;
  }
  &__title {
    font-style: normal;
    font-weight: 600;
    font-size: 20px;
    line-height: 25px;
  }

  &__desc {
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 20px;
  }

  &__price {
    font-style: normal;
    font-weight: 600;
    font-size: 24px;
    line-height: 30px;
  }
  &__delete {
    position: absolute;
    display: block;
    background-color: #ff8484;
    padding: 8px;
    width: 32px;
    height: 32px;
    border-radius: 8px;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
    right: -8px;
    top: -8px;
    cursor: pointer;
    opacity: 0;
    transition: opacity 0.2s ease-in-out;

    &:hover {
      opacity: 1;
    }
  }

  &__delete-img {
    width: 100%;
  }
  &:hover &__delete {
    opacity: 1;
  }
}
</style>
