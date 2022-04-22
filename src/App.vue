<template>

  <div id="app">

    <header>

      <HeaderComp :generi="this.arrayGeneri" @functionSearchGenre="methodSearchGenre" @functionSearchArtist="methodSearchArtist"/>

    </header>

    <main class="overflow-auto">

      <MainComp @generiPronti="ottieniGeneri" :genere="this.genere" :artist="this.artist"/>

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

    data(){

      return{

        genere: null,
        artist: null,
        arrayGeneri: []

      }

    },
    
    methods: {

      methodSearchGenre(genre){
        // Genere selezionato importato dal figlio HeaderComp
        this.genere = genre;
      },
      methodSearchArtist(artist){
        // Genere selezionato importato dal figlio HeaderComp
        this.artist = artist;
        console.log(this.artist)
      },
      ottieniGeneri(array){
        this.arrayGeneri = array;
      }

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
    }

    main {
      height: 90vh;
      background-color: $bg-main;
    }

  }
</style>