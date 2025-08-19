<script setup lang="ts">
import StartScreen from './components/StartScreen.vue';

const startQuiz = (topic) => {
 alert("Start Quiz :" + topic)   
}


</script>


<template>
<div id="app">
    <header>
        <div class="container">
            <img src="../src/assets/logo.png" alt="" class="logo"></img>
            <h1>Quiz Generator</h1>
        </div>
    </header>
    <StartScreen @start-quiz="startQuiz"></StartScreen>
</div>
</template>


