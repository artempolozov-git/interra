<template>
  <div id="app">
    <main-form></main-form>
  </div>
</template>

<script>
    import MainForm from "./components/MainForm";
    export default {
        name: 'App',
        components: {
            MainForm
        }
    }
</script>

<style>
  html, body {
    height: 100%;
  }
  body {
    font-family: Roboto;
    font-size: 16px;
    font-weight: normal;
    margin: 0;
  }
  #app {
    display: flex;
    justify-content: center;
    align-items: center;
    box-sizing: border-box;
    min-height: 100%;
    max-width: 1920px;
    background-color: #ffffff;
  }
  @font-face {
    font-family: Roboto;
    src: url('./assets/Roboto-Bold.ttf');
    font-weight: bold;
  }
  @font-face {
    font-family: Roboto;
    src: url('./assets/Roboto-Regular.ttf');
    font-weight: normal;
  }
</style>
