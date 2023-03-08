<template class="porHacer">

<h1>Por Hacer</h1>

            <div class="cards-container">
                <div v-for="(note,index) in notes" :key="index" class="card" :style="{backgroundColor: note.backgroundColor}">
                    <p class="main-text">{{ note.text }}</p>
                    <p class="date">{{ note.date.toLocaleDateString("en-eu") }}</p>
                    <button @click="showDetail(note.id)" class="detalle">Detalle</button>
                </div>
            </div>
            <!-- <div class="cards-container">
                <div  :key="index" class="card" :style="{backgroundColor: note.backgroundColor}">
                    <p class="main-text">{{ listaHecha.text }}</p>
                    <p class="date">{{ note.date.toLocaleDateString("en-eu") }}</p>
                </div>
            </div> -->
</template>

<script>
import { ref } from 'vue';

    
const listaHecha = ref(0);

export default {
    name: 'PorHacer',
    props:{
        notes:{
            type: Array
        },
        listaHecha:{
            type: Array
        }
    },
setup(props, {emit}){

const showDetail = (note) => {
    listaHecha.value = note
    emit("listaActualizada", listaHecha.value)
    
}

    return{
        showDetail 
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