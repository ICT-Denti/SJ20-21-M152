<template>
<main class="grid-container">
  <div class="fach">
    <h2>ABU</h2>
      <form @submit.prevent="addNote">
    <input v-model="newNote">
    <button>Add Note</button>    
  </form>
  <ul>
    <li v-for="note in notes" :key="note.id">
      {{ note.text }}
      <button @click="removeNote(note)">X</button>
    </li>
  </ul>
  </div>
  <div class="fach">
    <h2>M306</h2>
      <form @submit.prevent="addNote">
    <input v-model="newNote">
    <button>Add Note</button>    
  </form>
  <ul>
    <li v-for="note in notes" :key="note.id">
      {{ note.text }}
      <button @click="removeNote(note)">X</button>
    </li>
  </ul>
  </div>
  <div class="fach">
    <h2>NW</h2>
      <form @submit.prevent="addNote">
    <input v-model="newNote">
    <button>Add Note</button>    
  </form>
  <ul>
    <li v-for="note in notes" :key="note.id">
      {{ note.text }}
      <button @click="removeNote(note)">X</button>
    </li>
  </ul>
  </div>
  <div class="fach">
    <h2>M151</h2>
      <form @submit.prevent="addNote">
    <input v-model="newNote">
    <button>Add Note</button>    
  </form>
  <ul>
    <li v-for="note in notes" :key="note.id">
      {{ note.text }}
      <button @click="removeNote(note)">X</button>
    </li>
  </ul>
  </div>
  <div class="fach">
    <h2>M152</h2>
      <form @submit.prevent="addNote">
    <input v-model="newNote">
    <button>Add Note</button>    
  </form>
  <ul>
    <li v-for="note in notes" :key="note.id">
      {{ note.text }}
      <button @click="removeNote(note)">X</button>
    </li>
  </ul>
  </div>
  <div class="fach">
    <h2>M153</h2>
      <form @submit.prevent="addNote">
    <input v-model="newNote">
    <button>Add Note</button>    
  </form>
  <ul>
    <li v-for="note in notes" :key="note.id">
      {{ note.text }}
      <button @click="removeNote(note)">X</button>
    </li>
  </ul>
  </div>
  <div class="fach">
    <h2>Sport</h2>
      <form @submit.prevent="addNote">
    <input v-model="newNote">
    <button>Add Note</button>    
  </form>
  <ul>
    <li v-for="note in notes" :key="note.id">
      {{ note.text }}
      <button @click="removeNote(note)">X</button>
    </li>
  </ul>
  </div>
  <div class="fach">
    <h2>W&R</h2>
      <form @submit.prevent="addNote">
    <input v-model="newNote">    <button>Add Note</button> 
  </form>
  <ul>
    <li v-for="note in notes" :key="note.id">
      {{ note.text }}
      <button @click="removeNote(note)">X</button>
    </li>
  </ul>
  </div>
</main>
</template>


<script setup>
import { ref } from 'vue';


// give each note a unique id
let id = 0

const newNote = ref('')
const notes = ref([
  { id: id++, text: '3.0' },
  { id: id++, text: '6.0' },
  { id: id++, text: '5.5' }
])

function addNote() {
  notes.value.push({ id: id++, text: newNote.value })
  newNote.value = ''
}

function removeNote(note) {
  notes.value = notes.value.filter((t) => t !== note)
}
</script>

<style>
  @import '../assets/style.css';
</style>