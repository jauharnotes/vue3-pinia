<template>
  <h2>Ini Header</h2>
  <pre>{{ counter }}</pre>
  <pre>getters : {{ getCount }}</pre>
  <pre>getters : {{ doubleCount }}</pre>
  <pre>getters : {{ divideByTwo }}</pre>
  <pre>{{ getPokemon }}</pre>
</template>

<script setup>
import { computed } from 'vue';
import { useCounterStore } from '../stores/counter';
import { usePokemonStore } from '../stores/pokemon';

const counterStore = useCounterStore();
const pokemon = usePokemonStore();

const counter = computed(() => counterStore.count);
const getCount = computed(() => counterStore.getCount);
const doubleCount = computed(() => counterStore.doubleCount);
const divideByTwo = computed(() => counterStore.divideBy(2));
const getPokemon = computed(() => pokemon.pokemonDetails);

counterStore.$subscribe((mutations, state) => {
  console.log(mutations, state);
});
</script>
