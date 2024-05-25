<template>
  <section class="todo-app">
    <h1>TO-DO list</h1>
    <div class="todo-app-container">
      <div class="todo-list-input">
        <label>
          <input class="todo-input" placeholder="Що потрібно зробити?" v-model="newTodo">
          <button type="button" @click="addTodo">Додати в список</button>
        </label>
      </div>
      <ul v-for="todo in todos" :key="todo.id" class="todo-list">
        <li :class="{'is-completed': todo.done}" class="todo">
          <div class="todo-view">
            <label>
              <input class="toggle" type="checkbox" v-model="todo.done">
            </label>
            <h2>{{todo.text}}</h2>
            <button class="destroy" @click="removeTodo(todo.id)">Видалити</button>
          </div>
        </li>
      </ul>
      <div class="todo-list-remaining">
        {{notCompleted}} завдання залишилося
      </div>
    </div>
  </section>
</template>

<script setup>
import {computed, ref} from "vue";

let id = 0;

const newTodo = ref('')

const todos = ref([
    {id: id++, text: 'Вивчити Vue.js', done: false},
    {id: id++, text: 'Вивчити JS', done: false},
    {id: id++, text: 'Вивчити CSS', done: true},
    {id: id++, text: 'Вивчити HTML', done: true},
]);

function addTodo() {
  todos.value.push({id: id++, text: newTodo.value, done: false});
  newTodo.value = '';
}

function removeTodo(id) {
  todos.value = todos.value.filter(todo => todo.id !== id)
}

const notCompleted = computed(() => {
  return todos.value.filter(todo => !todo.done).length;
})
</script>
