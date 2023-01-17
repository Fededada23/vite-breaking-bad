<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue'
import CharactersList from './components/CharactersList.vue';
import { store } from './store.js';
// loaded
export default {
  components: {
    AppHeader,
    CharactersList
  },
  data() {
    return {
      store
    }
  },
  created() {
    this.getCardsYuGiOh();
  },
  methods: {
    getCardsYuGiOh() {
      axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php').then((response) => {
        store.charactersList = response.data
      })
    },
  },
}
</script>
<template lang="">
  <div class="container-yugi">
    <AppHeader class="p-5" message="Yu-Gi-Oh App"/>

    <main>
      <CharactersList />
    </main>
  </div>
</template>
<style lang="scss">
@use './styles/generals.scss' as *;
</style>