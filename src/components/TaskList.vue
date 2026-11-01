<script setup lang="ts">
    import TaskItem from './TaskItem.vue';

    const props = defineProps<{
        songsList: {
            id: number,
            nom: string,
            escoltada: boolean
        }[]
    }>();

    const emit = defineEmits<{
        complete: [id: number]
        delete: [id: number]
    }>();
</script>

<template>
    <ul>
        <TaskItem 
        v-for="song in songsList"
        :key="song.id"
        :song="song"
        @complete="emit('complete', $event)"
        @delete="emit('delete', $event)"
        />
    </ul>
</template>