<template>
    <div>
        <img class="logo" src="../img/undraw_ideas_flow_cy7b.svg" alt="Header pic">
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="What's you up for today?">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>

import uuid from 'uuid';

export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                id: uuid.v4(),
                title: this.title,
                completed: false
            }
            //Send up to parent
            this.$emit('add-todo', newTodo);

            this.title = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 10px;
        font-size: 1.1em;
        font-family: 'Neuton', serif;
    }

    input[type="submit"] {
        flex: 1;
        
    }

    .logo {
        max-width: 300px;
        display: block;
        margin-left: auto;
        margin-right: auto;
        width: 50%;
    }
</style>