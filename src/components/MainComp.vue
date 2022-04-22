<template>

    <!-- Se l'array non è stato popolato assegno le classi per centrale il loader -->
    <div :class="!isLoaded ? 'd-flex justify-content-center align align-items-center' : '' "
        id="contenitore" class="py-5">

        <!-- Se l'array è stato riempito allora mando in stampa -->
        <div v-if="isLoaded" class="container">

            <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-5">

                <!-- Stampo le singole card con un ciclio for -->
                <!-- <OneDisk v-for="(elem, index) in arrayDisk" :key="index" :poster="elem.poster" :title="elem.title"
                    :author="elem.author" :year="elem.year" /> -->
                <OneDisk v-for="(elem, index) in filter()" :key="index" :dati= "elem" />
        
            </div>
        </div>

        <!-- Loader di caricamento -->
        <div v-else class="loader"></div>

    </div>


</template>

<script>
    import axios from 'axios'

    // import components
    import OneDisk from "./partial/OneDisk.vue"

    export default {
        name: 'MainComp',

        components: {
            OneDisk
        },

        props:{
            genere: String,
            artist: String
        },

        data() {
            return {
                // Array dove metto i dati API di tutti i dischi
                arrayDisk: [],
                isLoaded: false,
                arrayGeneri: []
            }
        },

        created() {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
                    .then((res) => {

                        this.arrayDisk = res.data.response
                        this.isLoaded = true
                        
                        console.log(this.arrayDisk)

                        this.arrayDisk.forEach( (elem) => {

                            if(!this.arrayGeneri.includes(elem.genre)){

                                this.arrayGeneri.push(elem.genre)

                            }
                        } )
                        console.log(this.arrayGeneri)

                        this.$emit( 'generiPronti', this.arrayGeneri )
            })

        },

        methods: {

            // Metodo che filtra in base al genere
            filterGenre(){

                if(this.genere === null){

                    return this.arrayDisk;

                }else{

                    return this.arrayDisk.filter( (elem) => {

                        return elem.genre == this.genere

                    })

                }
            },
            // Metodo che filtra artista e genere
            filter(){
                if(this.artist == null){

                    return this.filterGenre();

                }else{

                    return this.filterGenre().filter( ( elem ) => {
                        return elem.author == this.artist
                    })
                }
            }
            
        }

    }
</script>

<style lang="scss" scoped>
    @import "../mixin.scss";

    #contenitore {
        @include center-x(70%);
        height: 100%;
    }

    // Classi per creare il loader
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
</style>