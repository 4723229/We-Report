#　第12回　Webエンジニアリング　レポート
##　学籍番号
4723229
## 実装したコード

### App.vue
```
<script setup lang=ts>

import { ref, computed } from 'vue';
import AddTodo from './components/AddTodo.vue';


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
    <section class="todo-app">
    <h2>Todos({{unfinishedTodos.length}})</h2>

    <ul>
      <li
      v-for="todo in todos"
      :key="todo.id"
      style="display: flex; align-items: center; gap: 0.5rem; margin:0.25rem 0;"
      >
      <input type="checkbox" v-model="todo.completed" />
      <span :style="{ textDecoration: todo.completed ? 'line-through' : 'none' }">
        {{ todo.title }}
      </span>   
      </li>
    </ul>

    
  </section>

  <AddTodo v-model:todos="todos" />

  </div>


</template>

```

### AddTodo.vue
```
<script setup lang=ts>
    import { ref } from 'vue';
    const todos = defineModel("todos");

    const newTitle = ref('');
    const nextId= ref(Math.max(0, ...todos.value.map(todo => todo.id))+1);

    function addTodo(){
        todos.value.push({ id: nextId.value++, title: newTitle.value, completed: false });
        newTitle.value = '';
    }

</script>

<template>
  <section>
    <h2>New Todo</h2>
    <div style="display: flex; align-items: center; gap: 0.5rem; margin: 0.25rem 0;">
      <input
        v-model="newTitle"
        placeholder="new Title"
        aria-label="new todo title"
      />
      <button v-on:click="addTodo" :disabled="!newTitle">Add</button>
    </div>


  </section>
    
</template>
```