<template>

    <div class="d-flex justify-content-between align-items-center h-100 px-3">
        <img src="../assets/Loghi/spotifyLogo.png" alt="" width="50px">

        <select class="form-select form-select-sm ms-auto w-25" aria-label=".form-select-lg example" v-model="genre">

            <option :value="null" selected>Choose the genre</option>
            <option v-for="(item, index) in genere" :key="index" 
                :value="item" 
                @change=" $emit( 'functionSearch', genre )"
                >
            {{item}}
            </option>

        </select>
    </div>


</template>

<script>
    export default {
        name: 'HeaderComp',

        data(){
            return{
               genere: ['Rock', 'Pop', 'Jazz', 'Metal'],
               genre: null
            }
        },

        created(){
            
        }
    }
</script>

<style lang="scss" scoped>
</style>