<template>
  <div class="container">
    <form class="form" id="form">
      <div class="logotype-wrapper">
        <img src="@/assets/interra.svg" class="img-logo">
      </div>
      <div class="form__head">
        <h1 class="form__title">
          Заявка на рассрочку
        </h1>
        <p class="form__subtitle text--large">
          Заполните контактные данные, чтобы оформить заявку на рассрочку
        </p>
      </div>
      <div class="form__body">
        <input v-model="products" name="product_name" class="form__element form__input" type="text" placeholder="Название услуги" required>
        <input v-model="prices" name="price" class="form__element form__input" type="text" placeholder="Стоимость" required>

        <div class="form__element form__button-wrapper">
          <div @click="getUrl" class="form__button">
            Cгенерировать ссылку
          </div>
        </div>
        <a :href="splitUrl" class="text--default" id="url" target="_blank">
          {{splitUrl}}
        </a>
      </div>
    </form>
  </div>
</template>

<script>
    import axios from 'axios'
    export default {
        name: "MainForm",
        data () {
            return {
                products: '',
                prices: '',
                splitUrl: '',
            }
        },
        methods: {
            getUrl() {
                let data = {
                    products: this.products,
                    prices: this.prices,
                };
                axios.post ('https://spinterra.online/users/split', data).then((response) => {
                    this.splitUrl = response.data.checkout_url;
                    console.log(response);
                })
            },
        },
    }
</script>

<style scoped>
  .container {
    width: 100%;
    max-width: 960px;
    margin: 0 auto;
    padding: 30px 15px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .form {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .form__head {
    text-align: center;
    margin-bottom: 40px;
  }
  .form__title {
    font-weight: bold;
    margin-bottom: 30px;
    color: #27272e;
  }
  .logotype-wrapper {
    width: auto;
    height: 70px;
    margin-bottom: 20px;
  }
  .logotype-wrapper .img-logo {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  .form__subtitle {
    max-width: 560px;
    font-weight: normal;
    color: #707070;
  }
  .form__body {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 520px;
    text-align: left;
  }
  .form__input {
    color: #030104;
    border: 2px solid #f5f4f3;
    background-color: #f5f4f3;
    margin: 0;
    height: 60px;
    padding: 0 20px;
    font-size: 16px;
    line-height: 1.33;
    width: 100%;
    box-sizing: border-box;
    outline: 0;
    border-radius: 0;
    font-family: Roboto;
  }
  .form__select-wrapper::after {
    content: " ";
    border-top-color: #030104;
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 6px 5px 0 5px;
    border-color: #000 transparent transparent transparent;
    position: absolute;
    right: 20px;
    top: 0;
    bottom: 0;
    margin: auto;
    pointer-events: none;
  }
  .form__element {
    margin-bottom: 25px;
    width: 100%;
  }
  .form__element p {
    padding-bottom: 5px;
  }
  .form__button {
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: Roboto;
    color: #ffffff;
    background-color: #5956e9;
    text-transform: uppercase;
    letter-spacing: 4px;
    border-radius: 10px;
    font-weight: normal;
    text-align: center;
    height: 70px;
    border: 0 none;
    font-size: 16px;
    padding-left: 60px;
    padding-right: 60px;
    cursor: pointer;
    margin: 0;
    box-sizing: border-box;
    outline: 0;
    max-width: 100%;
    transition: background-color 0.2s ease-in-out, color 0.2s ease-in-out, border-color 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
  }
  @media screen and (max-width: 768px) {
    .form__button {
      padding-left: 20px;
      padding-right: 20px;
      width: 100%;
    }
  }
  .form__button-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 25px;
    margin-bottom: 10px;
  }
  .form__credetials a {
    color: rgb(39, 39, 38);
  }
  .text--large {
    font-size: 20px;
  }
  .text--default {
    font-size: 18px;
  }

  #url {
    overflow-wrap: break-word;
    margin-top: 30px;
  }
  #url a {
    color: rgb(39, 39, 38);
    text-decoration: underline;
  }
  #url a:hover {
    color: blue;
    text-decoration: none;
  }
</style>
