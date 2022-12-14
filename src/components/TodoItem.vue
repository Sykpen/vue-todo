<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <input type="checkbox" v-on:change="todo.completed = !todo.completed">
            <strong>{{index + 1}}</strong>
            {{upperCase}}
        </span>
        <button class="deleteButton" v-on:click="$emit('remove-todo', todo.id)">
            &times
        </button>
    </li>
</template>

<script>
    export default {
        props: {
            todo: {
                type: Object,
                required: true,
            },
            index: Number
        },
        computed: {
            upperCase() {
                return this.todo.title.toUpperCase()
            }
        }
    }
</script>

<style scoped>
    li {
        border: 1px solid black;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 5px 10px;
        margin-bottom: 5px;
    }

    .deleteButton {
        background-color: red;
        border-radius: 50%;
        font-weight: bold;
    }

    input {
        margin-right: 15px;
    }

    .done {
        text-decoration: line-through;
    }
</style>