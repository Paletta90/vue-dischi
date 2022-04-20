<template>

  <div id="app">

    <header>

      <HeaderComp />

    </header>

    <main class="overflow-auto">

      <div>

        <MainComp />

      </div>

    </main>

  </div>

</template>

<script>
  import "bootstrap";

  // Import components
  import HeaderComp from "./components/HeaderComp.vue";
  import MainComp from "./components/MainComp.vue"

  export default {
    name: 'App',
    components: {
      HeaderComp,
      MainComp,
    },

  }
</script>

<style lang="scss">
  @import "./variabili.scss";
  @import "./mixin.scss";

  // Bootstrap 5
  @import "bootstrap/dist/css/bootstrap.min.css";

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;

    header {
      width: 100%;
      height: 10vh;
      background-color: $bg-header;
      @include flex(row, initial, center)
    }

    main {
      height: 90vh;
      background-color: $bg-main;
    }

    .loader {
      border: 16px solid #f3f3f3;
      border-radius: 50%;
      border-top: 16px solid green;
      width: 120px;
      height: 120px;
      -webkit-animation: spin 2s linear infinite;
      animation: spin 2s linear infinite;
    }

    @keyframes spin {
      0% {
        transform: rotate(0deg);
      }

      100% {
        transform: rotate(360deg);
      }
    }

  }
</style>