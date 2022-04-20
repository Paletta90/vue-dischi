<template>

    <div id="contenitore" class="py-5">

        <div class="container">

            <div class="row row-cols-2 row-cols-sm-3 row-cols-md-4 row-cols-lg-5">

                <!-- Stampo le singole card con un ciclio for -->
                <OneDisk v-for="(elem, index) in arrayDisk" :key="index" :poster="elem.poster" :title="elem.title"
                    :author="elem.author" :year="elem.year" />

            </div>

        </div>

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
                isLoaded: false,
            }
        },

        created() {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
                .then((res) => {
                    this.arrayDisk = res.data.response
                })
        },



    }
</script>

<style lang="scss" scoped>
    @import "../mixin.scss";

    #contenitore {
        @include center-x(70%);
    }
</style>