<script setup>
import { ref } from "vue";

const name = ref("");
const age = ref("");
const loc = ref("");
const formSubmitted = ref(false);
const openDy = ref(false);
const fillAgain = () => {
  formSubmitted.value = !formSubmitted.value;
  name.value = "";
  age.value = "";
  loc.value = "";
};

let id = 1;
const openTodoContainer = ref(false);
const favFood = ref("");
const favFoods = ref([]);
const addFavFood = () => {
  favFoods.value.push({ id: id++, name: favFood.value });
  favFood.value = "";
};
const removeFavFood = (food) => {
  favFoods.value = favFoods.value.filter((f) => f !== food);
};
</script>

<template>
  <div class="test">
    <h2>Home</h2>
    <br />
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusamus, esse.
      Odio assumenda iste reprehenderit, rerum laboriosam labore fugit atque
      voluptatem ullam molestias, dolores eos possimus facere, a eligendi hic
      repudiandae minima totam dolorum aperiam voluptate! Perspiciatis et nobis
      repellendus! Maiores ducimus libero quam possimus cum fugiat consequuntur
      recusandae adipisci nesciunt vero perferendis modi corporis sequi suscipit
      ipsa pariatur nulla, sint asperiores temporibus illo saepe id alias.
      Accusamus mollitia saepe enim, aperiam provident temporibus debitis illo
      reiciendis nam repellendus quas nobis!
    </p>
    <br />
  </div>
  <button
    type="submit"
    :class="{ redButton: openDy }"
    @click.prevent="openDy = !openDy"
  >
    {{ !openDy ? "Open" : "Close" }}
  </button>
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
      <p>
        Hello there {{ name }}. Your age is {{ age }}. You live in {{ loc }}
      </p>
      <input type="submit" value="Fill again" @click.prevent="fillAgain" />
    </div>
  </div>
  <button
    :class="{ redButton: openTodoContainer }"
    @click.prevent="openTodoContainer = !openTodoContainer"
  >
    {{ !openTodoContainer ? "Open Your Food List" : "Close" }}
  </button>
  <div v-if="openTodoContainer" class="todoContainer">
    <h3 v-if="favFoods.length === 0">Oops! Seems empty. Add one.</h3>
    <input type="text" v-model="favFood" />
    <button @click.prevent="addFavFood">Add</button>
    <ul>
      <h3 v-if="favFoods.length !== 0">Your favorite foods</h3>
      <li
        v-for="food in favFoods"
        :key="food.id"
      >
        {{ food.name }}
        <input
          type="submit"
          value="delete"
          @click.prevent="removeFavFood(food)"
        />
      </li>
    </ul>
  </div>
</template>
