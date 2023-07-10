<script setup>
import { ref } from 'vue'
import '../styles/Home.scss'

const name = ref('')
const age = ref('')
const loc = ref('')
const formSubmitted = ref(false)
const openDy = ref(false)

const fillAgain = () => {
    formSubmitted.value = !formSubmitted.value;
    name.value = ''
    age.value = ''
    loc.value = ''
}
</script>

<template>
    <div>
        <h2>Home</h2>
        <p>This is the hompage</p>
    </div>
    <button type="submit" @click.prevent="openDy = !openDy">{{!openDy?'Open this':'Close'}}</button>
    <div v-if="openDy">
        <form v-if="!formSubmitted">
            <label>What is your name?</label>
            <input v-model="name" />
            <label>How old are you?</label>
            <input type="number" v-model="age" />
            <label>Where do you live?</label>
            <input v-model="loc" />
            <input type="submit" @click.prevent="formSubmitted = !formSubmitted" />
        </form>
        <div v-if="formSubmitted">
            <p>Hello my name is {{ name }}. I am {{ age }} years old. I live in {{ loc }}</p>
            <input type="submit" value="Fill again" @click.prevent="fillAgain" />
        </div>
    </div>
</template>