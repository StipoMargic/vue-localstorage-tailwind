<template>
  <div class="container mt-40 mx-auto">
    <div class="w-full ">
      <form
        @submit.prevent="addTodo"
        class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4"
      >
        <div class="mb-4">
          <label
            class="block text-gray-700 text-sm font-bold mb-2"
            for="username"
          >
            Add Todo...
          </label>
          <input
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            type="text"
            placeholder="Add Todo..."
            v-model="newTodo"
          />
        </div>
        <div class="flex items-center justify-between">
          <button
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
            type="submit"
          >
            Add
          </button>
        </div>
      </form>
    </div>
    <ul>
      <li
        class="list-disc mx-40 "
        v-for="todo in todos"
        :key="todo.id"
        :class="{ done: todo.isDone }"
      >
        {{ todo.title }}
        <button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-4 focus:outline-none focus:shadow-outline"
          type="button"
          @click="removeTodo(todo, index)"
        >
          Delete
        </button>
        <button
          class=" bg-green-500 mx-4 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
          type="button"
          @click="finishTodo(todo)"
        >
          Finish
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "",
  data() {
    return {
      newTodo: "",
      todos: []
    };
  },
  watch: {
    todos: {
      handler() {
        localStorage.todo = JSON.stringify(this.todos);
      },
      deep: true
    }
  },
  mounted() {
    this.todos = JSON.parse(localStorage.todo);
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim().length == 0) {
        return;
      }

      this.todos.push({
        title: this.newTodo,
        isDone: false
      });
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
      alert("Todo removed");
    },
    finishTodo(todo) {
      this.todo.isDone = true;
    }
  }
};
</script>

<style>
.done {
  text-decoration: line-through red;
}
</style>
