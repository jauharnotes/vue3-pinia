<template>
  <h2>Ini Footer</h2>
  <br />

  <button @click="increment">Increment</button>
  <button @click="decrement">Decrement</button>
  <button @click="reset">Reset</button>

  <button @click="incrementWithAction">Increment with action</button>
  <button @click="decrementWithAction">Decrement with action</button>
  <button @click="incrementByWithAction(5)">Increment by with action</button>

  <button @click="getPokemon('ditto')">fect pokemon</button>
</template>

<script setup>
import { useCounterStore } from '../stores/counter';
import { usePokemonStore } from '../stores/pokemon';

const counter = useCounterStore();
const pokemon = usePokemonStore();

const increment = () => {
  counter.$patch((state) => {
    state.count++;
  });
};

const decrement = () => {
  counter.$patch((state) => {
    if (state.count != 0) {
      state.count--;
    }
  });
};

const reset = () => {
  counter.$reset();
};

const incrementWithAction = () => {
  counter.increment();
};

const decrementWithAction = () => {
  counter.decrement();
};

const incrementByWithAction = (amount) => {
  counter.incrementBy(amount);
};

const getPokemon = (name) => {
  pokemon.getPokemonDetails(name);
};
</script>
