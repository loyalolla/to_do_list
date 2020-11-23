<template>
  <div>
    <div class="header">
      <router-link class="bubbly" to="/">Home</router-link>
    </div>
    <AddTodo @add-todo="addTodo" />
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not Completed</option>
    </select>
    <hr />
    <Loader v-if="loading" />
    <TodoList
      v-else-if="filteredTodos.length"
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo"
    />
    <p v-else>No todos!</p>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
import Loader from "@/components/Loader";
export default {
  name: "app",
  data() {
    return {
      todos: [],
      loading: true,
      filter: "all",
    };
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=3")
      .then((response) => response.json())
      .then((json) => {
        setTimeout(() => {
          this.todos = json;
          this.loading = false;
        }, 1000);
      });
  },
  // watch: {
  //   filter(value) {
  //     console.log(value)
  //   }
  // },
  computed: {
    filteredTodos() {
      if (this.filter === "all") {
        return this.todos;
      }

      if (this.filter === "completed") {
        return this.todos.filter((t) => t.completed);
      }

      if (this.filter === "not-completed") {
        return this.todos.filter((t) => !t.completed);
      }
    },
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    },
  },
  components: {
    TodoList,
    AddTodo,
    Loader,
  },
};
</script>

<style scoped>
body {
  margin: 0;
  background: linear-gradient(#f2f2f6, #d3d3e7);
}
select {
  margin-bottom: 1rem;
  border-radius: 50px;
  background-color: rgba(71, 126, 232, 0.7);
  color: #fff;
}
.header {
  margin-bottom: 2rem;
}
.header:hover {
  outline-color: #2c3e50;
  outline-offset: 300px;
}
.bubbly {
  padding: 0.5rem 2rem;
  border-color: rgba(71, 126, 232, 0.7);
  color: #e1e8ee;
  border-radius: 50px;
  text-decoration: none;
  box-shadow: 0 0 40px 40px rgba(71, 126, 232, 0.7) inset,
    0 0 0 0 rgba(71, 126, 232, 0.7);
  -webkit-transition: all 150ms ease-in-out;
  transition: all 150ms ease-in-out;
  font-size: 1.1rem;
}
.bubbly:hover {
  box-shadow: 0 0 10px 0 rgba(71, 126, 232, 0.7) inset,
    0 0 10px 4px rgba(71, 126, 232, 0.7);
}
</style>
