<template>
  <main class="grid-container">
    <div class="fach" v-for="(noten, fach) in Faecher" :key="fach">
      <h2>
        {{ fach }}
      </h2>
      <form @keyup.enter="addNote($event, fach)">
        <input type="number" min="0" max="6"/>
         <button>Note hinzufügen</button> 
      </form>
      <ul>
        <li v-for="(note, index) in noten.noten" :key="index">
          {{ parseFloat(note).toFixed(2) }}
          <button @click="removeNote(fach, index)">X</button>
        </li>
        <li>
          <p class="schnitt"> Schnitt: {{ parseFloat(calculateAverageGrade(fach)).toFixed(2) }}</p>
        </li>
      </ul>
    </div>
      <form @keyup.enter="addSubject($event)">
        <label type="text">Name für Neues Fach: </label>
        <input type="text"/>
        <button>hinzufügen</button> 
      </form>
    <div>
      <p>Gesamter Notendurchschnitt:</p>
      <p class="schnitt">{{ parseFloat(roundHalf(calculateAverageGradeFromAllSubjects())).toFixed(2) }}</p>
    </div>
  </main>
</template>

<script setup>

import { ref } from 'vue';

const Faecher = ref({
  ABU: { noten: [3, 4.5, 5.3] },
  NW: { noten: [6, 2.7, 3.5] },
  Sport: { noten: [1.1, 3.6] },
  WuR: { noten: [5.3, 4.4] },
  M151: { noten: [2, 5, 4] },
  M152: { noten: [4, 3.8] },
  M153: { noten: [5, 5.8] },
  M306: { noten: [6, 5.9] },
});

function removeNote(fach, note) {
  Faecher.value[fach].noten.splice(note, 1);
}

function addNote(x, fach) {
  let newNote = Math.min(6, Math.max(1, parseInt(x.target.value)));
  Faecher.value[fach].noten.push(newNote);
}

function calculateAverageGrade(fach) {
  let sum = 0;
  for (let note of Faecher.value[fach].noten) {
    sum += note;
  }
  return sum / Faecher.value[fach].noten.length;
}

function calculateAverageGradeFromAllSubjects() {
  let sum = 0;
  let count = 0;
  for (let fach in Faecher.value) {
    for (let note of Faecher.value[fach].noten) {
      sum += note;
      count++;
    }
  }
  return sum / count;
}

function addSubject(x) {
  Faecher.value[x.target.value] = { noten: [] };
}

function roundHalf(num) {
    return Math.round(num*2)/2;
}
</script>

<style>
  @import '../assets/style.css';
</style>