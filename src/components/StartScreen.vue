
<script setup>
import { ref } from 'vue';

const topic = ref("");
const emit = defineEmits(['start-quiz'])
console.log("mahmud uz zaman");



</script>


<template>
    <section class="start-screen container">
        <h2>Choose a topic to testing your knowledge</h2>
        <input v-model="topic" type="text" placeholder="Enter Your topic..." />
        <button @click="emit('start-quiz', topic)" :disabled="!topic">Start Quiz</button>
    
    </section>
</template>
