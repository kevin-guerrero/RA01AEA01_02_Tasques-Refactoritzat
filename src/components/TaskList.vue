<script setup lang="ts">
    const props = defineProps<{
        songsList: {
            id: number,
            nom: string,
            escoltada: boolean
        }[]
    }>();

</script>

<template>
    <ul>
        <li 
            v-for="song in songsList" 
            :key="song.id"
        > 
        {{ song.nom }}
        
        </li>
    </ul>
</template>