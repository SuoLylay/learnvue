<template>
  <div style="text-align: center; margin-top: 50px">
    <h1>🧮 Add a Number</h1>

    <!-- Show current count -->
    <p>Current Count: {{ count }}</p>

    <!-- Input box for a number -->
    <input type="number" v-model.number="inputNumber" />

    <!-- Add button -->
    <button @click="count += inputNumber">Add</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// Count starts at 0
const count = ref(0)

// Input number starts at 1
const inputNumber = ref(1)
</script>

<style>
input {
  font-size: 16px;
  padding: 8px;
  width: 80px;
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 6px;
}
button {
  font-size: 16px;
  padding: 8px 16px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}
button:hover {
  background-color: #369870;
}
</style>
