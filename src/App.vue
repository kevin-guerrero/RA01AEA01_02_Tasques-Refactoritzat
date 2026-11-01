<script setup lang="ts">
    import { computed, ref } from 'vue';
    import TaskList from './components/TaskList.vue';
    const songs = ref([
    {
        id: 1,
        nom: "Ultraviolence",
        escoltada: false
    },
    {
        id: 2,
        nom: "Cinnamon girl",
        escoltada: true
    },
    {
        id: 3,
        nom: "Chasing Cars",
        escoltada: false
    },
    {
        id: 4,
        nom: "Hey Jude",
        escoltada: true
    }
    ]);

    // Variable per les cançons que falten per escoltar
    const isListened = ref(false);

    // Funció per mostrar canços que falten per escoltar
    const songsListened = computed(() => {
        if(isListened.value === false) {
            return songs.value
        }else {
            return songs.value.filter(song => song.escoltada === false)
        }
    });

    const changeStatus = (songSelect: number) => {
        const song = songs.value.find(song => song.id === songSelect);

        if (song) {
            song.escoltada = !song.escoltada;
        }
    };

    function deleteSong(id: number) {
        songs.value = songs.value.filter(song => song.id !== id);
    }

</script>

<template>
    <TaskList
        :songsList="songsListened"
        @complete="changeStatus"
        @delete="deleteSong"
    />
</template>

<style scoped></style>
