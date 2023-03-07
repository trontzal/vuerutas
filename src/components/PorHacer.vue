<template>

<h1>hola</h1>
<p>Hacer que las tarjetas se puedan borrar y arrastrar a una casilla de "hecho"</p>
<div class="cards-container">
                <div v-for="note in notes" :key="id" class="card" :style="{backgroundColor: note.backgroundColor}">
                    <p class="main-text">{{ note.text }}</p>
                    <p class="date">{{ note.date.toLocaleDateString("en-eu") }}</p>
                </div>
            </div>
</template>

<script>
export default {
    name: 'PorHacer',
    props:{
        notes:{
            type: Array
        }
    }
   
}
console.log()


</script>

<style>
.card{
        width: 12rem;
        height: 15rem;
        background-color:aquamarine;
        padding: 1rem;
        border-radius: 15px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        margin-right: 2rem;
        margin-bottom: 2rem;
    }

    .cards-container{
        display: flex;
        flex-wrap:wrap;
        width: 50%;
    }

</style>