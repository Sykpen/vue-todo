<template>
    <div>
        <ul>
            <TodoItemVue v-for="(todo, i) of todos" v-bind:todo="todo" v-bind:index="i" v-on:remove-todo="removeTodo">
            </TodoItemVue>
        </ul>
    </div>
</template>

<script>
import TodoItemVue from './TodoItem.vue';
export default {
    props: ['todos'],
    components: {
        TodoItemVue
    },
    methods: {
        removeTodo(id) {
            this.$emit('remove-todo', id);
        }
    }
}
</script>

<style scoped>
ul {
    list-style: none;
    margin: 0;
    padding: 0
}

</style>