<script setup>
  import { useQuery, useResult } from '@vue/apollo-composable'
  import allCharactersQuery from './graphql/allCharacters.query.gql'

  const { result } = useQuery(allCharactersQuery)
  const characters = useResult(result, null, data => data.characters.results)
</script>

<template>
  <div class="characters">
    <div v-for="(character, index) in characters" :key="index">
      <img :src="character.image" :alt="character.name" />
      <p>{{ character.name }}</p>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.characters {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
