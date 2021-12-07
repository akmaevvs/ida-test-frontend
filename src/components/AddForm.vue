<template>
  <form class="add-form" @submit.prevent="console.log('click')">
    <div class="input-block">
      <form-label :required="true">Наименование товара</form-label>
      <form-input :placeholder="'Наименование товара'" required />
    </div>
    <div class="input-block">
      <form-label :required="false">Описание товара</form-label>
      <form-input :placeholder="'Введите описание товара'" />
    </div>
    <div class="input-block">
      <form-label :required="true">Ссылка на изображение товара</form-label>
      <form-input :placeholder="'Введите ссылку'" required />
    </div>
    <div class="input-block">
      <form-label :required="true">Цена товара</form-label>
      <form-input :placeholder="'Введите цену товара'" required />
    </div>
    <div class="input-block input-block--button">
      <form-button>Добавить товар</form-button>
    </div>
  </form>
</template>

<script>
import FormInput from "@/components/UI/FormInput.vue";
import FormLabel from "@/components/UI/FormLabel.vue";
import FormButton from "@/components/UI/FormButton.vue";
export default {
  name: "add-form",
  components: {
    FormInput,
    FormLabel,
    FormButton
  }
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

    &--button {
      margin-top: 14px;
    }
  }
}
</style>