<script setup lang="ts">
    const props = defineProps<{
        song: {
            id: number
            nom: string
            escoltada: boolean
        }
    }>()

    const emit = defineEmits<{
        complete: [id: number]
        delete: [id: number]
    }>()
</script>

<template>
    <li>
        {{ song.nom }} -
        <button v-if="song.escoltada" @click="emit('complete', song.id)">
            Escoltada
        </button>
        <button v-else @click="emit('complete', song.id)" >  
            No escoltada
        </button>
        -
        <button type="button" @click="emit('delete', song.id)">
            🗑️
        </button>
    </li>
</template>