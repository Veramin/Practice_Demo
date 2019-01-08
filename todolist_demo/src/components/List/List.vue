<template>
    <ul class="todo-main">
        <Item
            v-for="(todo, index) in todos"
            :key="index"
            :index="index"
            :todo = "todo"
            :delToDo = "delToDo"
        />
    </ul>
</template>

<script>

import Item from "../Item/Item"

export default {
    name: "List",
    components: {
        Item,
    },
    props: {
        todos: Array,
        delToDo: Function
    }
}
</script>

<style scoped>
    .todo-main {
        width: 820px;
        height: 100%;
        background-color: #fff;
        margin: 0 auto;
        padding: 0;

    }
</style>
