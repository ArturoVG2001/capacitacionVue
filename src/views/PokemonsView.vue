<script setup>
import { RouterLink } from 'vue-router';
import { useGetData } from '../composables/getData';
import { useCounterStore } from '@/store/counter';

const useCounter = useCounterStore();

const { data, getData, loading, error } = useGetData();

getData("https://pokeapi.co/api/v2/pokemon");
</script>

<template>
    <h1>Pokemons</h1>
    <p v-if="loading">Cargando informacion...</p>
    <div class="alert alert-danger mt-2" v-if="error">{{ error }}</div>
    <div v-if="data" class="list-group">
        <ul>
            <li v-for="pokemon in data.results" class="list-group-item">
                <router-link :to="`/pokemons/${pokemon.name}`">
                    {{ pokemon.name }}
                </router-link>
            </li>
        </ul>
        <div class="mt-2 mb-4">
            <button :disabled="!data.previous" class="btn btn-success me-2"
                @click="getData(data.previous)">Previous</button>
            <button :disabled="!data.next" class="btn btn-primary" @click="getData(data.next)">Next</button>
        </div>
    </div>
</template>