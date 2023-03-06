<template>
    <PorHacer />
    <main>
        <div v-show="showModal" class="overlay">
            <div  class="modal">
                <textarea v-model="newNote" name="notes" id="notes" cols="30" rows="10"></textarea>
                <button @click="addNote">Nota nueva</button>
                <button @click="showModal = false" class="cerrar">Cerrar</button>
            </div>
        </div>
        <div class="container">
            <header>
                <h2>Notas</h2>
                <button @click="showModal = true">+</button>
            </header>
            <div class="cards-container">
                <div v-for="note in notes" :key="id" class="card" :style="{backgroundColor: note.backgroundColor}">
                    <p class="main-text">{{ note.text }}</p>
                    <p class="date">{{ note.date.toLocaleDateString("en-eu") }}</p>
                </div>
            </div>
        </div>
    </main>
   
</template>

<script setup>
    import PorHacer from '../components/PorHacer.vue';
    import { ref } from "vue";



const showModal = ref(false)
const newNote = ref("")
const notes = ref([])

const addNote =() => {
    notes.value.push({
        id: Math.floor(Math.random() * 10000000),
        text: newNote.value, 
        date: new Date(),
        backgroundColor: getRandomColor()  
    })
    showModal.value = false
    newNote.value = ""
}
function getRandomColor() {
  return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
}

</script>

<style scoped>

    main{
        height: 100vh;
        width: 100vw;
        text-align: left;
    }

    .container{
        max-width: 60rem;
        padding: 1rem;
        margin: 0 auto;
    }
    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    h2{
        font-weight: bold;
        margin-bottom: 0.5rem;
        font-size: 5rem;
    }

    header button{
        border:none;
        width: 3rem;
        height: 3rem;
        cursor: pointer;
        background-color: rgb(21, 20, 20);
        border-radius: 100%;
        color: white;
        font-size: 2rem;
    }

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

    .date{
        font-size: 0.8rem;
        font-weight: bold;
    }

    .cards-container{
        display: flex;
        flex-wrap:wrap;
    }

    .overlay{
        position: absolute;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.77);
        z-index: 10;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .modal{
        width: 40rem;
        height: 20rem;
        background-color: white;
        border-radius: 10px;
        padding:1rem;
        position: relative;
        display: flex;
        flex-direction: column;
    }

    .modal button{
        padding: 0.1rem;
        font-size:2rem;
        width:100%;
        background-color: blueviolet;
        border: none;
        color: white;
        cursor: pointer;
        margin-top: 1rem;
    }

    .modal .cerrar{
        background-color: red;
        margin-top: 1rem;
    }
</style>