<script lang="ts">
import { store } from '../store.js';
export default {
    data() {
        return {
            store
        }
    },
    computed: {
        numberResults() {
            return store.cards.length
        }
    }
}
</script>
<template lang="">
    <div>
        <h2>
            Trovati {{numberResults}} risultati
        </h2>
    </div>
</template>
<style lang="scss" scoped>
</style>