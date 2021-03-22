<template>
<div>
    <h1 class="container">{{mensaje}}</h1>
    <the-footer />
</div>
</template>
<script lang="ts">
import Vue from 'vue'
import axios from 'axios';
import env from '../config/env';
import TheFooter from '~/components/TheFooter.vue'
export default Vue.extend({
    components: {
        TheFooter,
        },
        data(){
        return{
            mensaje:'holas'
        }
    },
    created(){
        axios.get(`${env.endpoint}/albums`).then(response =>{
            console.log(response);
        })
    }
})
</script>

<style scoped>

</style>