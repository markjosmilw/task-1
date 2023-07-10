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
    <div class="test">
        <h2>Contact</h2>
        <p>Since this page doesn't have contact information. You can try putting yours.</p>
            <br/>
    </div>
    <form class="formContact" v-if="!formSubmitted">
        <label>What is email address?</label>
        <input type="text" v-model="email" />
        <label>What is you phone number?</label>
        <input type="text" v-model="phone" />
        <input type="submit" @click.prevent="formSubmitted = !formSubmitted" />
    </form>
    <div v-if="formSubmitted">
        <p>Your email address is {{ email }}. Your contact number is {{ phone }}.</p>
        <input type="submit" value="Fill again" @click.prevent="fillAgain" />
    </div>
</template>