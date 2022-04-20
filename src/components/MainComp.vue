<template>

    <!-- Se l'array non è stato popolato assegno le classi per centrale il loader -->
    <div :class="arrayDisk.length == 0 ? 'd-flex justify-content-center align align-items-center' : '' "
        id="contenitore" class="py-5">

        <!-- Se l'array è stato riempito allora mando in stampa -->
        <div v-if="arrayDisk.length > 0" class="container">

            <div class="row row-cols-2 row-cols-sm-3 row-cols-md-4 row-cols-lg-5">

                <!-- Stampo le singole card con un ciclio for -->
                <OneDisk v-for="(elem, index) in arrayDisk" :key="index" :poster="elem.poster" :title="elem.title"
                    :author="elem.author" :year="elem.year" />

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

        data() {
            return {
                // Array dove metto i dati API di tutti i dischi
                arrayDisk: [],
            }
        },

        // methods: {
        //     callAxios: function () {
        //         axios.get("https://flynn.boolean.careers/exercises/api/array/music")
        //             .then((res) => {
        //                 this.arrayDisk = res.data.response
        //                 console.log(this.arrayDisk.length)
        //             })
        //     }
        // },

        created() {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
                    .then((res) => {
                        this.arrayDisk = res.data.response
                        console.log(this.arrayDisk.length)
            })

            // setTimeout(this.callAxios, 3000)
        },

    }
</script>

<style lang="scss" scoped>
    @import "../mixin.scss";

    #contenitore {
        @include center-x(70%);
        height: 100%;
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
</style>