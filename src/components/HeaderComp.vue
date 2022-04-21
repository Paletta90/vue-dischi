<template>

    <div class="d-flex justify-content-between align-items-center h-100 px-3">
        <img src="../assets/Loghi/spotifyLogo.png" alt="" width="50px">

        <select class="form-select form-select-sm ms-auto w-25" aria-label=".form-select-lg example" v-model="value">
            <option :value="null" selected>Choose the genre</option>
            <option v-for="(item, index) in genere" :key="index" :value="index">{{item}}</option>
            <!-- <option selected>Open this select menu</option>
            <option value="1">Rock</option>
            <option value="2">Pop</option>
            <option value="3">Jazz</option>
            <option value="4">Metal</option> -->
        </select>
    </div>


</template>

<script>
    export default {
        name: 'HeaderComp',

        data(){
            return{
               genere: ['Rock', 'Pop', 'Jazz', 'Metal'],
               value: null
            }
        },

        created(){
            
        }
    }
</script>

<style lang="scss" scoped>
</style>