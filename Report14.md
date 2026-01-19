# 第14回　Webエンジニアリング演習　レポート
## 学籍番号
4723229

## 実装したコード

### index.ts
```
import { createRouter, createWebHistory } from 'vue-router'
import TodoListView from '../views/TodoListView.vue'
import About from '../views/About.vue'
import TodoDetail from '../views/TodoDetail.vue'

const routes = [
    { path: '/', name: 'TodoList', component: TodoListView },
    { path: '/about', name: 'About', component: About },
    { path: '/todos/:id', name: 'TodoDetail', component: TodoDetail },
]

export const router = createRouter({
    history: createWebHistory(),
    routes,
})

export default router
```

### TodoDetail.vue
```
<script setup lang="ts">
    import { useTodoStore } from '../stores/todoStore';
    import { useRoute } from 'vue-router';
    const todoStore = useTodoStore();
    const route = useRoute();
    const todoId = Number(route.params.id);
</script>

<template>
    <section class="todo-detail">
        <h2>Todo Number: {{ todoId }}</h2>
        <p>
            やること: {{
                todoStore.todos.find((todo) => todo.id === todoId)?.title 
            }}
        </p>
        <p>
            状　　態: {{
                todoStore.todos.find((todo) => todo.id === todoId)?.completed ? '完了' : 'まだやってない'
            }}
        </p>
    </section>
</template>
```
### About.vue
```
<script setup lang="ts">
    import { useTodoStore } from '../stores/todoStore';
</script>

<template>
    <h1>About This App</h1>
    <p>やることはやる</p>
</template>
```