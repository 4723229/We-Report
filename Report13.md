# 第13回　Webエンジニアリング演習　レポート
## 学籍番号
4723229

## 実装したコード
### App.vue
```
<script setup lang=ts>

import AddTodo from './components/AddTodo.vue';
import { useTodoStore } from './stores/todoStore';

const todoStore = useTodoStore()
</script>

<template>
  <div id="app">
    <section class="todo-app">
    <h2>Todos</h2>
    <ul>
      <li
        v-for= "todo in todoStore.todos"
        :key= "todo.id"
        style= "display: flex; align-items: center; gap: 0.5rem; margin:0.25rem 0;"
      >
      <input type="checkbox" v-model="todo.completed" />
      <span :style="{ textDecoration: todo.completed ? 'line-through' : 'none' }">
        {{ todo.title }}
      </span>   
      <button v-on:click="todoStore.deleteTodo(todo.id)">Remove</button>
      </li>
    </ul>
  </section>

  <AddTodo/>

  </div>


</template>

```

### todoStore
```
import { defineStore } from 'pinia'
import { ref } from 'vue'

interface Todo {
    id: number
    title: string
    completed: boolean
    }

export const useTodoStore = defineStore('todos', () => {
    let serialId = 4
    
    const todos = ref<Todo[]>([
        { id: 1, title: 'Buy groceries', completed: false },
        { id: 2, title: 'Write report', completed: true },
        { id: 3, title: 'Call Alice', completed: false },
    ])

    const addTodo = (title: string) => {
        const newTodo: Todo = {
            id: serialId++,
            title: title,
            completed: false,
        }
        todos.value.push(newTodo)
    }

    const deleteTodo = (id: number) => {
        todos.value = todos.value.filter(todo => todo.id !== id)

    }

    return { todos, addTodo, deleteTodo }
})
```