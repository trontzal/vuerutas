<template class="porHacer">

<h1>Por Hacer</h1>

            <div class="cards-container">
                <div v-for="(note,index) in notes" :key="index" class="card" :style="{backgroundColor: note.backgroundColor}">
                    <p class="main-text">{{ note.text }}</p>
                    <p class="date">{{ note.date.toLocaleDateString("en-eu") }}</p>
                    <button @click="showDetail(note)" class="detalle">Detalle</button>
                </div>
            </div>

</template>

<script>
import { pushScopeId } from 'vue';
import { reactive } from 'vue';

export const listaHecha = reactive([]);

export default {
    name: 'PorHacer',
    props:{
        notes:{
            type: Array
        }
    },
  methods: {
        // deleteNote: function(index) {
        // this.notes.splice(index, 1);
        // }
        showDetail(note) {
         listaHecha.push(note)
         console.log(listaHecha)
    }
    }
}



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

    }

</style>