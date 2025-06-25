<template>
    <button v-on:click="incrementClicks">Aantal Clicks</button>
    <button v-on:click="updateFirstName">Verander Voornaam</button>
    <input v-model="person.firstName" type="text" />
    <button v-on:click="updateCountry">Verander Land</button>
    <input v-model="person.country" type="text" />

    <p>Aantal clicks: {{ clicks }}</p>
    <p>Voornaam: {{ person.firstName }}</p>
    <p>Land: {{ person.country }}</p>

    <ul>
        <li v-for="(task, index) in tasks" :key="index">
            Taak: {{ task.name }}, Voltooid?: {{ task.completed }}
            <button @click="toggleCompletedTask(task)">Toggle status</button>
        </li>
    </ul>
</template>

<script setup>
import {ref, reactive} from 'vue';

// Opdracht 4
const clicks = ref(0);
const person = reactive({
    firstName: '',
    country: '',
});

const incrementClicks = () => {
    clicks.value++;
};

const updateFirstName = () => {
    if (updateFirstName.value) {
        person.firstName = updateFirstName.value;
    }
};

const updateCountry = () => {
    if (updateCountry.value) {
        person.country = updateCountry.value;
    }
};

// Opdracht 5
const tasks = ref([
    {name: 'Boodschappen doen', completed: false},
    {name: 'Afwassen', completed: true},
    {name: 'Hond uitlaten', completed: false},
]);

const toggleCompletedTask = task => {
    task.completed = !task.completed;
};
</script>

<style scoped></style>
