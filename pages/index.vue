<template>
<div>
    <the-header />
    <div class="columns m-6">
        <div class="column m-3 pt-6 has-text-centered">
            <h1 class="title ">Encuentra entrevistas a tu medida con los mejores restaurantes de México</h1>
            <h2>Lorem ipsum dolor</h2>
            <p class="has-text-left mt-4">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Corporis quasi 
                optio libero magnam ad facere odio expedita illum! Voluptatum architecto veritatis deleniti et, quidem 
                expedita minus. Non unde vero molestias.</p>
            <p class="has-text-left mt-4">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Corporis quasi 
                optio libero magnam ad facere odio expedita illum! Voluptatum architecto veritatis deleniti et, quidem 
                expedita minus. Non unde vero molestias.</p>
        </div>
        <div class="column is-three-fifths">
            <div class="is-flex is-justify-content-center">
                <figure class="">
                    <img class="ml-6" src="~/assets/images/hero.png" alt="image_hero">
                </figure>
            </div>
        </div>
    </div>
    <div class="columns m-6">
        <div class="column is-one-third is-text-center">
            <div class="col-text">
                <h3 class="has-text-centered is-size-4 mb-4">Fácil Registro</h3>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Maiores illo sed veniam fugit? 
                    Adipisci velit suscipi Lorem ipsum dolor sit amet consectetur adipisicing elit.
                    Maiores illo sed veniam fugit? Adipisci velit suscipi</p>
            </div>
        </div>
        <div class="column">
            <div class="col-text">
                <h3 class="has-text-centered is-size-4 mb-4">Entrevistas en movimiento</h3>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Maiores illo sed veniam fugit? 
                    Adipisci velit suscipi Lorem ipsum dolor sit amet consectetur adipisicing elit.
                    Maiores illo sed veniam fugit? Adipisci velit suscipi</p>
            </div>
        </div>
        <div class="column">
            <div class="col-text">
                <h3 class="has-text-centered is-size-4 mb-4">Un solo sitio, toda la industria</h3>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Maiores illo sed veniam fugit? 
                    Adipisci velit suscipi Lorem ipsum dolor sit amet consectetur adipisicing elit.
                    Maiores illo sed veniam fugit? Adipisci velit suscipi</p>
            </div>    
        </div>
    </div>
    <the-footer />
</div>
</template>
<script lang="ts">
import Vue from 'vue'
import axios from 'axios';
import env from '../config/env';
import TheHeader from '~/components/TheHeader.vue'
import TheFooter from '~/components/TheFooter.vue'
export default Vue.extend({
    components: {
        TheFooter,
        TheHeader,
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
.col-text{
    width: 80%;
}

</style>