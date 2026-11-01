<script setup lang="ts">
    const props = defineProps<{
        song: {
            id: number
            nom: string
            escoltada: boolean
        }
    }>()
</script>

<template>
    <li>
        {{ song.nom }} - {{  song.escoltada }}
    </li>
</template>