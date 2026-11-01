<script setup lang="ts">
import { ref } from 'vue';

const newSong = ref('');

const emit = defineEmits<{
    'add-song': [songName: string]
}>();

function submitSong() {

    if (newSong.value.trim() === '') {
        newSong.value = ''
        return;
    }

    emit('add-song', newSong.value);
    newSong.value = '';
}
</script>

<template>
    <form @submit.prevent="submitSong">
        <input v-model="newSong" placeholder="Introdueix una nova cançó">
        <button type="submit">Afegir</button>
    </form>
</template>