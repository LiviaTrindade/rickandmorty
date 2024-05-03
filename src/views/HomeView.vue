

<script setup>
import { onMounted, reactive, ref } from 'vue';
import ListCharacters from '../components/ListCharacters.vue'

let characters = reactive(ref([]));

onMounted(async () => {
  let url = "https://rickandmortyapi.com/api/character";
  try {
    while (url) {
      const response = await fetch(url);
      const data = await response.json();
      characters.value = [...characters.value, ...data.results];
      url = data.info.next;
    }
  } catch (error) {
    console.error(error);
  }
});

</script>

<template>
  <div class="character-container">
    <div v-for="character in characters" :key="character.id" class="character-card">
      <img :src="character.image" :alt="character.name" class="character-image">
      <div class="character-info">
        <p class="character-name">{{ character.name }}</p>
        <p><b>Status:</b> {{ character.status }}</p>
        <p><b>Espécie:</b> {{ character.species }}</p>
        <p><b>Gênero:</b> {{ character.gender }}</p>
        <p><b>Localização atual:</b> {{ character.location.name }}</p>
        <p><b>Episódios:</b> {{ character.episode.length }}</p>
      </div>
    </div>
  </div>
</template>



<style scoped>

.character-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  background-color: #181818;
}

.character-card {
  width: 200px;
  padding: 10px;
  border-radius: 8px;
  margin-top: 10px;
  margin-left: 45px;
  box-shadow: 0 4px 6px rgba(0, 183, 255);
  background-color: #11c7ff;
  transition: box-shadow 0.3s ease;
}

.character-card:hover {
  box-shadow: 0 8px 12px rgb(0, 255, 21);
}

.character-image {
  width: 100%;
  border-radius: 8px;
}

.character-info {
  margin-top: 10px;
  font-size: 14px;
  font-family: 'Comic Sans MS', cursive, sans-serif;
}

.character-info p {
  margin: 5px 0;
}

.character-name {
  font-weight: bold;
}
</style>


