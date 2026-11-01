<script setup lang="ts">
    import TaskItem from './TaskItem.vue';

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
        <TaskItem 
        v-for="song in songsList"
        :key="song.id"
        :song="song"
        />
    </ul>
</template>