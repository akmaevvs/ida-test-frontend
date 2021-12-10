<template>
  <div class="inner-container">
    <top-header @select-sort-state-event="SelectSortState" />
    <section class="content-section">
      <add-form
        class="add-form"
        :productListLength="productListLength"
        @add-product-event="AddProduct"
      />
      <transition name="slide-fade">
        <product-list
          v-if="productList.length > 0"
          @delete-product-event="DeleteProduct"
          @change-default-img="SetDefault"
          :productList="productList"
        />
        <div class="empty-product-block" v-else>
          <h4 class="empty-product-block__text">Товары отсутствуют</h4>
        </div>
      </transition>
    </section>
  </div>
</template>

<script>
import TopHeader from "@/components/TopHeader.vue";
import AddForm from "@/components/AddForm.vue";
import ProductList from "@/components/ProductList.vue";
import defaultImgProductCard from "@/assets/img/default_img_product_card.jpg";

export default {
  name: "App",
  components: { TopHeader, AddForm, ProductList },
  data() {
    return {
      defaultImgProductCard,
      productList: [],
      productListLength: "0",
      sortState: {
        id: "default",
        titleState: "По умолчанию",
      },
    };
  },
  mounted() {
    if (localStorage.productList) {
      this.productList = JSON.parse(localStorage.productList);
    }
  },
  watch: {
    productList: {
      deep: true,
      handler(val) {
        localStorage.productList = JSON.stringify(val);
      },
    },
  },
  methods: {
    SetDefault(id) {
      this.productList = this.productList.filter((product) => {
        if (product.id === id) {
          product.img = this.defaultImgProductCard;
        }
        return product;
      });
    },
    AddProduct(product) {
      this.productList.unshift(product);
      this.productListLength = this.productList.length.toString();

      this.SelectSortState(this.sortState);
    },
    DeleteProduct(id) {
      this.productList = this.productList.filter((product) => {
        if (product.id !== id) {
          return product;
        }
      });
    },
    SelectSortState(state) {
      this.sortState = state;
      if (state.id == "by-name") {
        this.productList.sort((a, b) =>
          a.title > b.title ? 1 : a.title < b.title ? -1 : 0
        );
      } else if (state.id == "min-price") {
        this.productList.sort((a, b) =>
          parseInt(a.price.replaceAll(" ", "")) >
          parseInt(b.price.replaceAll(" ", ""))
            ? 1
            : parseInt(a.price.replaceAll(" ", "")) <
              parseInt(b.price.replaceAll(" ", ""))
            ? -1
            : 0
        );
      } else if (state.id == "max-price") {
        this.productList.sort((a, b) =>
          parseInt(a.price.replaceAll(" ", "")) <
          parseInt(b.price.replaceAll(" ", ""))
            ? 1
            : parseInt(a.price.replaceAll(" ", "")) >
              parseInt(b.price.replaceAll(" ", ""))
            ? -1
            : 0
        );
      } else {
        this.productList.sort((a, b) =>
          a.id < b.id ? 1 : a.id > b.id ? -1 : 0
        );
      }
    },
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap");
:root {
  --default-text-color: #3f3f3f;
  --placeholder-text-color: #b4b4b4;
  --default-button-text-color: #b4b4b4;
  --input-label-text-color: #49485e;
  --font-size-button-input: 12px;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  position: relative;
  background-color: #fffefbcc;
  // overflow-x: hidden;
}
input,
button {
  outline: none;
  border: none;
  background: none;
  padding: 0;
  font-family: "Source Sans Pro", Avenir, Helvetica, Arial, sans-serif;
}
input::placeholder {
  font-family: "Source Sans Pro", Avenir, Helvetica, Arial, sans-serif;
  color: var(--placeholder-text-color);
}
#app {
  font-family: "Source Sans Pro", Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #3f3f3f;
}

// fade effect
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease-in-out;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

// add/delete product
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease-in-out;
}
.list-enter,
.list-leave-to {
  opacity: 0;
  transform: translateY(100%);
}

// appearence products
.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.5s ease-in-out;
}
.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(100%);
  opacity: 0;
}

.inner-container {
  display: flex;
  flex-direction: column;
  width: 100%;
  max-width: 1440px;
  gap: 16px;
  margin: 0 auto;
  padding-bottom: 32px;

  & .content-section {
    display: flex;
    justify-content: space-between;
    gap: 16px;
    padding: 0 32px 0 32px;
    width: 100%;
    position: relative;

    & .empty-product-block {
      display: flex;
      justify-content: center;
      width: 100%;
      align-items: center;

      &__text {
        font-size: 20px;
      }
    }
  }
  & .add-button-block {
    position: fixed;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    bottom: 20px;
    margin: 0 auto;
    margin-left: -32px;
    // left: 0;
    // right: 0;

    & .add-button {
      background-color: green;
      padding: 8px 20px;
      border-radius: 10px;
      box-shadow: 0px 3px 10px #000;
    }
  }
}

@media screen and (max-width: 600px) {
  .content-section {
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 30px;
  }
}
</style>
