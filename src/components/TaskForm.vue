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

<style scoped>
form {
    display: flex;
    justify-content: center;
    gap: 8px;
}

input {
    min-width: 0;
    flex: 1;
    padding: 10px 12px;
    border: 1px solid #cbd5e1;
    border-radius: 6px;
    font: inherit;
}

button {
    padding: 10px 14px;
    border: 0;
    border-radius: 6px;
    background: #2563eb;
    color: white;
    font: inherit;
    cursor: pointer;
}

button:hover {
    background: #1d4ed8;
}
</style>