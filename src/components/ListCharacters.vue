<template>
    <div>
      <div v-for="character in characters" :key="character.id">
        <img :src="character.image" alt="character.name">
        <p>Nome: {{ character.name }}</p>
        <p>Status: {{ character.status }}</p>
        <p>Espécie: {{ character.species }}</p>
        <p>Gênero: {{ character.gender }}</p>
        <p>Localização atual: {{ character.location.name }}</p>
        <p>Episódios: {{ character.episode.length }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        characters: []
      }
    },
    mounted() {
      fetch('https://rickandmortyapi.com/api/character')
       .then(response => response.json())
       .then(data => {
          this.characters = data.results;
        })
       .catch(error => console.error(error));
    }
  }
  </script>