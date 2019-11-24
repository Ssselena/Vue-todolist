 <template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    
  </div>
</template>

<script>

import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';

export default {
  name: 'app',
  components: {
     Header,
     Todos,
     AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Clean my room",
          completed: false
        },

        {
          id: 2,
          title: "Pay rent",
          completed: false
        },

        {
          id: 3,
          title: "Create TodoApp with Vue",
          completed: false
        }
      ]
    }
    },
    methods: {
      deleteTodo(id) {
        this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    }
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #6c63ff;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;

  }

  @import url('https://fonts.googleapis.com/css?family=Neuton|Proza+Libre&display=swap');
</style>
