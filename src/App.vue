<template>
  
  
  <ul>
    <li>{{  person.firstName }}</li>
    <li>{{  person.name }}</li>
    <li>{{  person.age }}</li>
  </ul>

  <button @click.prevent="randomAge">Changer age</button>
</template>

<script setup>
import {ref} from 'vue'

const person = ref({
  firstName: 'John',
  name: 'Doe',
  age: 20  
})

const randomAge = () => {
  person.value.age = Math.round(Math.random() * 100)
}

</script>

<style>
</style>
