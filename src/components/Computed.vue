<script setup>
import { reactive, computed, ref } from 'vue';

const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery',
  ],
});

// a computed ref
const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No';
});
/*********************************************************************/
const firstName = ref('John');
const lastName = ref('Doe');

const fullName = computed({
  // getter
  get() {
    return firstName.value + ' ' + lastName.value;
  },
  // setter
  set(newValue) {
    // Note: we are using destructuring assignment syntax here.
    [firstName.value, lastName.value] = newValue.split(' ');
  },
});
fullName.value = 'Vladimir Putin';
</script>

<template>
  <h1>Computed</h1>
  <p>Has published books:</p>
  <span>{{ publishedBooksMessage }}</span>
  <hr />
  <p>{{ fullName }}</p>
  <span>{{ firstName }}</span>
</template>
