#　第11回　Webエンジニアリング演習　レポート
## 学籍番号
4723229

## 実装したコード
```
<script setup lang=ts>

import { ref, computed } from 'vue';

const name = ref('Vue 3 with TypeScript');
type Todo = { id: number; title: string; completed: boolean };

const todos = ref<Todo[]>([
  { id: 1, title: 'Buy groceries', completed: false },
  { id: 2, title: 'Write report', completed: true },
  { id: 3, title: 'Call Alice', completed: false },
]);

const unfinishedTodos = computed(
  () => todos.value.filter((todo) => !todo.completed)
);
</script>

<template>
  <div id="app">
    <h2>Todos({{unfinishedTodos.length}})</h2>

    <ul>
      <li
      v-for="todo in todos"
      :key="todo.id"
      styel="display: flex; align-items: center; gap: 0.5rem; margin:0.25rem 0;"
      >
      <input type="checkbox" v-model="todo.completed" />
      <span :style="{ textDecoration: todo.completed ? 'line-through' : 'none' }">
        {{ todo.title }}
      </span>   
      </li>
    </ul>
  </div>
</template>
```