<template>
<h1> hecho </h1>
        <div class="cards-container">
            <div v-for="(note,index) in notes" :key="id" class="card" :style="{backgroundColor: note.backgroundColor}">
                <p class="main-text">{{ note.text }}</p>
                <p class="date">{{ note.date.toLocaleDateString("en-eu") }}</p>
                <button @click="deleteNote(index)" class="eliminar">Eliminar</button>
            </div>
        </div>
</template>

<script>


</script>

<style>


</style>