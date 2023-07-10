<script setup>
import { ref } from 'vue'

const email = ref('')
const phone = ref('')
const formSubmitted = ref(false)

const fillAgain = () => {
    formSubmitted.value = !formSubmitted.value;
    email.value = ''
    phone.value = ''
}
</script>

<template>
    <h2>Contact</h2>
    <form v-if="!formSubmitted">
        <label>What is email address?</label>
        <input required v-model="email" />
        <label>What is you phone number?</label>
        <input v-model="phone" />
        <input type="submit" @click.prevent="formSubmitted = !formSubmitted" />
    </form>
    <div v-if="formSubmitted">
        <p>My email address is {{ email }}. My contact number is {{ phone }}.</p>
        <input type="submit" value="Fill again" @click.prevent="fillAgain" />
    </div>
</template>