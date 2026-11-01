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

<style scoped>
ul {
    display: grid;
    gap: 10px;
    margin: 20px 0 0;
    padding: 0;
    list-style: none;
}
</style>