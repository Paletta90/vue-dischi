<template>

    <div class="col d-flex text-center g-3">

        <!-- Card del disco -->
        <div class="bg-card p-2">

            <img :src="poster" alt="" class="img-fluid mb-3">
            <h5 class="text-white fw-bold mb-3">{{title}}</h5>
            <h6 class="text-secondary">{{author}}</h6>
            <h6 class="text-secondary">{{year}}</h6>

        </div>

    </div>

</template>

<script>
    export default {
        name: 'OneDisk',

        props: {
            poster: String,
            title: String,
            author: String,
            year: String,
        }
    }
</script>

<style lang="scss" scoped>
    @import "../../variabili.scss";

    .bg-card{
        background-color: $bg-card;
    }
</style>