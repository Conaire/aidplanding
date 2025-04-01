<script setup>
import WelcomeItem from './WelcomeItem.vue'
import AIDatePicker from 'ai-datepicker/vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
import Prism from 'prismjs';
import 'prismjs/components/prism-javascript';
import {ref} from "vue";
const openReadmeInEditor = () => fetch('/__open-in-editor?file=README.md')
import 'prismjs/themes/prism-tomorrow.css';

const react = `
import React, { useState } from 'react';
import AIDatepicker from 'ai-datepicker';

export default function App() {
  const [selectedDate, setSelectedDate] = useState(null);

  return (
    <div>
      <h1>Select a Date</h1>
      <AIDatepicker
        value={selectedDate}
        onChange={setSelectedDate}
      />
      {selectedDate && <p>You selected: {selectedDate}</p>}
    </div>
  );
}

`




const reactCode = ref(Prism.highlight(react, Prism.languages.javascript, 'javascript'))


const vuel = `
<template>
  <div>
    <h1>Select a Date</h1>
    <AIDatepicker v-model="selectedDate" />
    <p v-if="selectedDate">You selected: {{ selectedDate }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import AIDatepicker from 'ai-datepicker'

const selectedDate = ref(null)
<\/script>
`


const vueCode = ref(Prism.highlight(vuel, Prism.languages.javascript, 'javascript'))


const vanilla = `
<script src="https://cdn.example.com/ai-datepicker.js"><\/script>
Date: <input type="text" id="date" data-aidp="date">
<button data-aidp-button="date">✔</button>
<div data-aidp-result="date"></div>
`


const vanillaCode = ref(Prism.highlight(vanilla, Prism.languages.javascript, 'javascript'))

</script>

<template>
  <WelcomeItem style="padding-top: 160px;">
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading><span style="font-size: 1.5em">Try it out!</span></template>
    <div style="color: #5f5e5e; margin-bottom: 10px">eg: “Next Friday” • “3 days from now” • “1st Monday of May” • “31 Aug 1990”</div>

    <div class="aidp-container">
      <AIDatePicker />
    </div>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
<!--      <ToolingIcon />-->
    </template>
    <template #heading>React</template>
    <pre><code class="language-js" v-html="reactCode"></code></pre>

  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
<!--      <EcosystemIcon />-->
    </template>
    <template #heading>Vue</template>
    <pre><code class="language-js" v-html="vueCode"></code></pre>

  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
<!--      <CommunityIcon />-->
    </template>
    <template #heading>Vanilla JS</template>

    <pre><code class="language-js" v-html="vanillaCode"></code></pre>

  </WelcomeItem>

  <WelcomeItem>
    <div class="aidp-section">
      <h2>📣 Events</h2>
      <p>You can hook into key lifecycle moments of the date fetching process:</p>

      <table class="aidp-table">
        <thead>
        <tr>
          <th>Prop</th>
          <th>Description</th>
        </tr>
        </thead>
        <tbody>
        <tr>
          <td><code>fetching</code></td>
          <td>Called right before the date fetch begins</td>
        </tr>
        <tr>
          <td><code>selected</code></td>
          <td>Called with the parsed date when fetch succeeds</td>
        </tr>
        <tr>
          <td><code>error</code></td>
          <td>Called with an error object if parsing fails</td>
        </tr>
        <tr>
          <td><code>done</code></td>
          <td>Called after fetch completes (with or without error)</td>
        </tr>
        </tbody>
      </table>
    </div>

    <div class="aidp-section">
      <h2>⚙️ Options</h2>
      <p>You can pass optional props to influence how the AI interprets and returns dates:</p>

      <table class="aidp-table">
        <thead>
        <tr>
          <th>Prop</th>
          <th>Description</th>
        </tr>
        </thead>
        <tbody>
        <tr>
          <td><code>region</code></td>
          <td>Geographic region or locale (e.g. <code>"US"</code>, <code>"UK"</code>, <code>"JP"</code>)</td>
        </tr>
        <tr>
          <td><code>format</code></td>
          <td>Output date format string (e.g. <code>"YYYY-MM-DD"</code>)</td>
        </tr>
        <tr>
          <td><code>hint</code></td>
          <td>Extra context to guide the AI (e.g. <code>"wedding dates"</code>)</td>
        </tr>
        </tbody>
      </table>
    </div>

  </WelcomeItem>

</template>

<style>
pre {
  background-color: #1e1e1e;
  padding: 1em;
  border-radius: 8px;
  overflow-x: auto;
}


.aidp-container {
  display: flex;
  align-items: flex-start;
  gap: 0.5rem;
  flex-wrap: wrap;
  max-width: 400px;
  font-family: sans-serif;
}

.aidp-date {
  flex: 1;
  padding: 0.5rem 0.75rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 8px;
}

.aidp-button {
  background-color: #4caf50;
  border: none;
  color: white;
  font-size: 1.2rem;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.aidp-button:hover {
  background-color: #45a045;
}

.aidp-result {
  width: 100%;
  margin-top: 0.5rem;
  min-height: 2.5rem; /* fixed height */
  padding: 0.5rem;
  background-color: #f6f6f6;
  border-radius: 6px;
  font-size: 0.95rem;
  color: #333;
  box-sizing: border-box;
  transition: all 0.2s ease-in-out;
}

/* Optional fade effect */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.2s;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
.aidp-section {
  font-family: system-ui, sans-serif;
  margin-bottom: 2rem;
}

.aidp-section h2 {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
}

.aidp-section p {
  margin-bottom: 1rem;
  color: #444;
}

.aidp-table {
  width: 100%;
  border-collapse: collapse;
  background: #fff;
  box-shadow: 0 1px 3px rgba(0,0,0,0.05);
  border-radius: 6px;
  overflow: hidden;
}

.aidp-table th,
.aidp-table td {
  text-align: left;
  padding: 0.75rem 1rem;
  border-bottom: 1px solid #eee;
  vertical-align: top;
}

.aidp-table th {
  background-color: #f9f9f9;
  font-weight: 600;
  color: #222;
}

.aidp-table td code {
  background: #f4f4f4;
  padding: 0.2em 0.4em;
  border-radius: 4px;
  font-size: 0.95em;
}

.aidp-table tr:last-child td {
  border-bottom: none;
}
</style>