<template>

    <div class="d-flex justify-content-between align-items-center h-100 px-3">

        <img src="../assets/Loghi/spotifyLogo.png" alt="" width="50px">

        <div class="d-flex">
            <select class="form-select form-select-sm ms-auto me-3" aria-label=".form-select-lg example" v-model="genre"
                @change=" $emit( 'functionSearchGenre', genre )">

                <option :value="null" selected>Choose the genre</option>
                <option v-for="(item, index) in generi" :key="index" :value="item">
                    {{item}}
                </option>

            </select>

            <select class="form-select form-select-sm ms-auto" aria-label=".form-select-lg example" 
                    v-model="artist"
                    @change=" $emit( 'functionSearchArtist', artist ) "
                    >

                <option :value="null" selected>Choose the artist</option>
                <option v-for="(item, index) in artisti" :key="index" :value="item">
                    {{item}}
                </option>

            </select>
        </div>

    </div>


</template>

<script>
    export default {
        name: 'HeaderComp',

        props:{
            arrayDisk: [],
            generi:[],
            artisti:[]
        },
        data() {
            return {
                genre: null,
                artist: null
            }
        }

    }
</script>

<style lang="scss" scoped>

    select {
        width: 100%;
    }
</style>