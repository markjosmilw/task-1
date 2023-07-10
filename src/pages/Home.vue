<script setup>
import { ref } from 'vue'


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
    <div class="test">
        <h2>Home</h2>
        <br />
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusamus, esse. Odio assumenda iste reprehenderit,
            rerum laboriosam labore fugit atque voluptatem ullam molestias, dolores eos possimus facere, a eligendi hic
            repudiandae minima totam dolorum aperiam voluptate! Perspiciatis et nobis repellendus! Maiores ducimus libero
            quam possimus cum fugiat consequuntur recusandae adipisci nesciunt vero perferendis modi corporis sequi suscipit
            ipsa pariatur nulla, sint asperiores temporibus illo saepe id alias. Accusamus mollitia saepe enim, aperiam
            provident temporibus debitis illo reiciendis nam repellendus quas nobis!</p>
        <br />
    </div>
    <button type="submit" :class="{ redButton: openDy }" @click.prevent="openDy = !openDy">{{ !openDy ? 'Open' : 'Close'
    }}</button>
    <div v-if="openDy" class="parentOF">
        <form v-if="!formSubmitted" class="openForm">
            <label>What is your name?</label>
            <input type="text" v-model="name" />
            <label>How old are you?</label>
            <input type="number" v-model="age" />
            <label>Where do you live?</label>
            <input type="text" v-model="loc" />
            <input type="submit" @click.prevent="formSubmitted = !formSubmitted" />
        </form>
        <div v-if="formSubmitted" class="closeForm">
            <p>Hello there {{ name }}. Your age is {{ age }}. You live in {{ loc }}</p>
            <input type="submit" value="Fill again" @click.prevent="fillAgain" />
        </div>
    </div>
</template>