<template>
  <div class="product-list">
    <div class="product-card">
      <img class="product-card__img" :src="defaultLogo" alt />
      <div class="product-card__info">
        <h4 class="product-card__title">Наименование товара</h4>
        <p
          class="product-card__desc"
        >Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк</p>
        <p class="product-card__price">10 000 руб.</p>
      </div>
    </div>
    <div class="product-card">
      <img class="product-card__img" :src="defaultLogo" alt />
      <div class="product-card__info">
        <h4 class="product-card__title">Наименование товара</h4>
        <p
          class="product-card__desc"
        >Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк</p>
        <p class="product-card__price">10 000 руб.</p>
      </div>
    </div>
    <div class="product-card">
      <img class="product-card__img" :src="defaultLogo" alt />
      <div class="product-card__info">
        <h4 class="product-card__title">Наименование товара</h4>
        <p
          class="product-card__desc"
        >Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк</p>
        <p class="product-card__price">10 000 руб.</p>
      </div>
    </div>
    <div class="product-card">
      <img class="product-card__img" :src="defaultLogo" alt />
      <div class="product-card__info">
        <h4 class="product-card__title">Наименование товара</h4>
        <p
          class="product-card__desc"
        >Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк</p>
        <p class="product-card__price">10 000 руб.</p>
      </div>
    </div>
    <div class="product-card">
      <img class="product-card__img" :src="defaultLogo" alt />
      <div class="product-card__info">
        <h4 class="product-card__title">Наименование товара</h4>
        <p
          class="product-card__desc"
        >Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк</p>
        <p class="product-card__price">10 000 руб.</p>
      </div>
    </div>
    <div class="product-card">
      <img class="product-card__img" :src="defaultLogo" alt />
      <div class="product-card__info">
        <h4 class="product-card__title">Наименование товара</h4>
        <p
          class="product-card__desc"
        >Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк</p>
        <p class="product-card__price">10 000 руб.</p>
      </div>
    </div>
  </div>
</template>

<script>
import defaultLogo from "@/assets/img/default_logo.png";
export default {
  name: "product-list",
  data() {
    return {
      defaultLogo
    };
  }
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

  .product-card {
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 332px;

    background: #fffefb;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
      0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;

    cursor: pointer;

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
  }
}
</style>