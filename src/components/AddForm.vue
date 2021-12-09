<template>
  <form class="add-form" @submit.prevent="AddProduct" novalidate>
    <div class="input-block">
      <form-label :required="true">Наименование товара</form-label>
      <input
        type="text"
        v-model="product.title"
        class="input-block__input input-block__input input-block__input--valid"
        :placeholder="'Наименование товара'"
        required
        @input="RemoveNoValid"
      />
      <span class="valid-exception valid-exception--none"
        >Поле является обязательным</span
      >
    </div>
    <div class="input-block">
      <form-label :required="false">Описание товара</form-label>
      <input
        type="text"
        v-model="product.desc"
        class="input-block__input input-block__input--valid"
        :placeholder="'Введите описание товара'"
      />
    </div>
    <div class="input-block">
      <form-label :required="true">Ссылка на изображение товара</form-label>
      <input
        type="text"
        v-model="product.img"
        class="input-block__input input-block__input--valid"
        :class="{ 'input-block--no-valid-img': !validImgUrl }"
        :placeholder="'Введите ссылку'"
        required
        @input="RemoveNoValid"
      />
      <span class="valid-exception valid-exception--none"
        >Поле является обязательным</span
      >
      <span v-if="!validImgUrl" class="valid-exception valid-exception--block"
        >Введите корректную ссылку на изображение</span
      >
    </div>
    <div class="input-block">
      <form-label :required="true">Цена товара</form-label>
      <input
        type="text"
        v-model="product.price"
        class="input-block__input input-block__input--valid"
        :placeholder="'Введите цену товара'"
        required
        @input="
          RemoveNoValid($event);
          InsertSpace();
        "
      />
      <span class="valid-exception valid-exception--none"
        >Поле является обязательным</span
      >
    </div>
    <div class="input-block input-block--button">
      <form-button type="submit" :valid="valid">Добавить товар</form-button>
    </div>
  </form>
</template>

<script>
import FormLabel from "@/components/UI/FormLabel.vue";
import FormButton from "@/components/UI/FormButton.vue";
export default {
  name: "add-form",
  components: {
    // FormInput,
    FormLabel,
    FormButton,
  },
  data() {
    return {
      product: {
        id: null,
        title: null,
        desc: null,
        img: null,
        price: null,
      },
      valid: false,
      validImgUrl: true,
      alph: "1234567890 ",
    };
  },
  props: {
    productListLength: {
      type: String,
      default: "",
    },
  },
  watch: {
    product: {
      deep: true,
      handler(newProduct) {
        if (
          newProduct.title &&
          newProduct.img &&
          newProduct.price &&
          this.ValidateImgUrl(newProduct.img)
        ) {
          this.valid = true;
        } else {
          this.valid = false;
        }
        if (newProduct.img && !this.ValidateImgUrl(newProduct.img)) {
          this.validImgUrl = false;
          this.valid = false;
        } else {
          this.validImgUrl = true;
        }
      },
    },
  },
  methods: {
    InsertSpace() {
      this.product.price = this.product.price
        .replace(" ", "")
        .replace(/(\d{1,3}(?=(\d{3})+(?:\.\d|\b)))/g, "$1 ")
        .replace(/[^0-9 ]/gm, "");
      console.log(this.product.price);
    },
    RemoveNoValid($event) {
      $event.target.classList.remove("input-block--no-valid");
      $event.target.nextSibling.classList.remove("valid-exception--block");
      $event.target.nextSibling.classList.add("valid-exception--none");
    },
    ValidateImgUrl(url) {
      return url.match(/(\/|\.)(png|jpg)/gm) != null;
    },
    MakeId() {
      let id = "";
      const alphabet =
        "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";

      for (let i = 0; i < 5; i++)
        id +=
          this.productListLength +
          alphabet.charAt(Math.floor(Math.random() * alphabet.length));

      return id;
    },
    AddProduct() {
      if (this.valid) {
        this.product.id = this.MakeId();
        this.$emit("add-product-event", this.product);
        this.product = {
          title: null,
          desc: null,
          img: null,
          price: null,
        };
        this.valid = false;
        // } else {
        //   this.validImgUrl = false;
        // }
      } else {
        const requiredInputs = document.querySelectorAll("input[required]");

        requiredInputs.forEach((input) => {
          if (!input.value) {
            input.classList.add("input-block--no-valid");
            input.nextSibling.classList.remove("valid-exception--none");
            input.nextSibling.classList.add("valid-exception--block");
          }
        });

        console.log(requiredInputs);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.add-form {
  display: flex;
  flex-direction: column;
  gap: 16px;
  background-color: #fffefb;
  box-shadow: 0px 20px 30px #0000000a, 0px 6px 10px #00000005;
  border-radius: 4px;
  padding: 24px;
  box-sizing: border-box;
  width: 100%;
  max-width: 332px;
  height: 100%;
  position: sticky;
  top: 24px;

  & .input-block {
    display: flex;
    flex-direction: column;
    gap: 4px;
    width: 100%;
    position: relative;
    &__input {
      background: #fffefb;
      box-shadow: 0px 2px 5px #0000001a;
      border-radius: 4px;
      padding: 10px 16px;

      font-style: normal;
      font-weight: normal;
      font-size: 12px;
      line-height: 15px;

      width: 100%;
      transition: border-color 0.2s ease-in-out;
      &:focus {
        border-color: #bbb7b8;
      }
      &--valid {
        border: 1px solid #00000000;
      }
    }
    &--button {
      margin-top: 14px;
    }

    &--no-valid {
      border: 1px solid #ff8484;
    }
    &--no-valid-img {
      border: 1px solid #ff8484;
    }

    & .valid-exception {
      display: none;
      color: #ff8484;
      font-style: normal;
      font-weight: normal;
      font-size: 8px;
      line-height: 10px;
      letter-spacing: -0.02em;

      &--none {
        display: none;
      }

      &--block {
        display: block;
      }
    }
  }
}
</style>
