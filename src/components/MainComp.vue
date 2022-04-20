<template>
    <div id="contenitore" class="py-5">
        <div class="container">

            <div class="row row-cols-5">
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
                arrayDisk: []
            }
        },

        created() {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
                .then((res) => {
                    console.log(res.data.response[0])

                    this.arrayDisk = res.data.response
                })
        }
    }
</script>

<style lang="scss" scoped>

    @import "../mixin.scss";

    #contenitore{
        @include center-x(70%);
    }
</style>