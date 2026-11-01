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
        {{ song.nom }}
        <button v-if="song.escoltada" @click="emit('complete', song.id)">
            Escoltada
        </button>
        <button v-else @click="emit('complete', song.id)" >  
            No escoltada
        </button>
        <button type="button" @click="emit('delete', song.id)">
            🗑️
        </button>
    </li>
</template>

<style scoped>
li {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    padding: 12px;
    border: 1px solid #e2e8f0;
    border-radius: 8px;
    background: #f8fafc;
}

button {
    padding: 7px 10px;
    border: 0;
    border-radius: 5px;
    background: #e2e8f0;
    color: #1e293b;
    font: inherit;
    cursor: pointer;
}

button:hover {
    background: #cbd5e1;
}

button:last-child {
    flex-shrink: 0;
}
</style>