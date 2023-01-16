<script>
import axios from 'axios'
import AppHeader from './components/AppHeader.vue';
import Select from './components/Select.vue';
import CharactersList from './components/CharactersList.vue';
import { store } from './store.js';
export default {
  components: {
    AppHeader,
    CharactersList,
    Select,
  },
  data() {
    return {
      store
    }
  },
  created() {
    this.getCharacters();
  },
  methods: {
    getCharacters() {
      axios.get(store.url).then((response) => {
        store.charactersList = response.data.data
        setTimeout(() => {
          store.loading = false
        }, 3000)
      })
    }
  }
}
</script>
<template lang="">
  <div class="container-yugi">
    <AppHeader message="Yu-Gi-Oh App"/>
    <AppSelect />
    <main>
      <CharactersList />
    </main>
  </div>
</template>
<style lang="scss">
@use './styles/generals.scss' as *;
</style>