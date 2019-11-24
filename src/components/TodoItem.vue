<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p>
        <input type="checkbox" v-on:change="markComplete">
        {{todo.title}}
        <button @click="$emit('del-todo', todo.id)" class="del">delete</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete() {
            
            this.todo.completed = !this.todo.completed;
            
        }
    }
}
</script>

<style scoped>
    .todo-item {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
        font-family: 'Neuton', serif;
        font-size: 1.4em;
    }

    .is-complete {
        text-decoration: line-through;
        color: grey;
    }

    .del {
        background: #D90368;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 25px;
        cursor: pointer;
        float: right;
    }

    input[type="checkbox"] {
        
        margin-right: 10px;
        
    }
</style>