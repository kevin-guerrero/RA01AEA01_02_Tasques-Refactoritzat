<script setup lang="ts">
    import { computed, ref } from 'vue';
    import TaskForm from './components/TaskForm.vue';
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

    const addSong = (songName: string) => {
        songs.value.push({
            id: Date.now(),
            nom: songName,
            escoltada: false
        });
    }

    function deleteSong(id: number) {
        songs.value = songs.value.filter(song => song.id !== id);
    }

</script>

<template>
    <main class="app">
        <section class="song-manager">
            <h1>Gestor de cançons</h1>
            <TaskForm @add-song="addSong" />
            <TaskList
                :songsList="songsListened"
                @complete="changeStatus"
                @delete="deleteSong"
            />
        </section>
    </main>
</template>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    min-width: 320px;
    min-height: 100vh;
    background: #f1f5f9;
    color: #1e293b;
    font-family: Arial, sans-serif;
}

#app {
    min-height: 100vh;
}
</style>

<style scoped>
.app {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 24px;
}

.song-manager {
    width: min(100%, 520px);
    padding: 32px;
    border-radius: 12px;
    background: white;
    box-shadow: 0 4px 16px rgb(15 23 42 / 10%);
}

h1 {
    margin: 0 0 24px;
    text-align: center;
}

@media (max-width: 480px) {
    .song-manager {
        padding: 24px 18px;
    }
}
</style>
