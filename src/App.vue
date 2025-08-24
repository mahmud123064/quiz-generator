<script setup lang="ts">
import StartScreen from './components/StartScreen.vue';
import { GoogleGenerativeAI } from "@google/generative-ai";
import { ref } from 'vue';

const question = ref("")
const startQuiz = async (topic) => {
  try {

    question.value = "Loading values ..."
    // Correctly initialize the library with your API key
    const genAI = new GoogleGenerativeAI("AIzaSyCcGJHQhsSZxUwQMUPV7txe2xPUMkZace4");

    async function main() {
      // Choose the correct model name (e.g., "gemini-pro")
      const model = genAI.getGenerativeModel({ model: "gemini-1.5-flash" });

      const prompt = `create a multi-choise quiz generator ${topic}`;

      // Generate content
      const result = await model.generateContent(prompt);
      const response = await result.response;
      const text = response.text();

      console.log(question.value = text);
      
    }

    await main();
  } catch (error) {
    console.error("An error occurred:", error);
  }
};

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
    <p>{{ question }}</p>
</div>
</template>


