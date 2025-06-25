<template>
    <button v-on:click="incrementClicks">Aantal Clicks</button>
    <button v-on:click="updateFirstName">Verander Voornaam</button>
    <input v-model="person.firstName" type="text" />
    <button v-on:click="updateCountry">Verander Land</button>
    <input v-model.lazy="person.country" type="text" />

    <p>Aantal clicks: {{ clicks }}</p>
    <p>Voornaam: {{ person.firstName }}</p>
    <p>Land: {{ person.country }}</p>

    <ul>
        <li v-for="(task, index) in tasks" :key="index">
            Taak: {{ task.name }}, Voltooid?: {{ task.completed }}
            <button @click="toggleCompletedTask(task)">Toggle status</button>
        </li>
    </ul>
    <p><strong>Voeg persoon toe</strong></p>
    <label for="nieuweNaam">Naam:</label>
    <br />
    <input id="nieuweNaam" type="text" v-model.trim="newName" />
    <br />
    <label for="nieuweLeeftijd">Leeftijd:</label>
    <br />
    <input id="nieuweLeeftijd" type="text" v-model.number="newAge" />
    <br />
    <button @click="addPerson(newName, newAge)">Add Person</button>
    <br />
    <p>List of People:</p>
    <ul>
        <li v-for="(persoon, index) in people" :key="index">
            {{ persoon }}
        </li>
    </ul>
    <p>List of Children:</p>
    <ul>
        <li v-for="(child, index) in children" :key="index">
            {{ child }}
        </li>
    </ul>
</template>

<script setup>
import {ref, reactive, computed} from 'vue';

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

//Opdracht 6 (het wordt wellicht wat onoverzichtelijk, voor de volgende opdracht gebruik ik een nieuw project :-) )
const people = ref([
    {name: 'Jan', age: 12},
    {name: 'Piet', age: 20},
]);

const addPerson = function (newName, newAge) {
    const newPerson = {name: newName, age: newAge};
    people.value.push(newPerson);
};

const children = computed(() => {
    return people.value.filter(persoon => persoon.age < 18);
});
</script>

<style scoped></style>
