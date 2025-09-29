<template>
    <ul uk-tab>
        <router-link to="/page-2"><li class="uk-active"><a href="#">Left</a></li></router-link>
        <li><a href="#">Item</a></li>
        <li><a href="#">Item</a></li>
        <li class="uk-disabled"><a>Disabled</a></li>
    </ul>

    <button @click="callApi" class="uk-button uk-button-default">Appeler</button>
    <div v-for="movie in movies" :key="movie.title">
        {{ movie.title }}
    </div>

</template>

<script setup>

import {ref} from 'vue';
import log from 'electron-log/renderer';

const movies = ref([]);

async function callApi() {
    // TODO : Afficher chargement

    //appeler l'API


    const res = await fetch('https://raw.githubusercontent.com/Chocolaterie/EniWebService/main/api/movies.json');

    const data = await res.json();

    if (data.length != 0) {
        movies.value = data
        log.info('Le JSON a été récupéré');
    }else {
        log.error('Le JSON a pas été récupéré');
    }


    //Récupérer le JSON

    // TODO : Fermer le chargement
}

</script>