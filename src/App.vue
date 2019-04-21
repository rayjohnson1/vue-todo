<template>
  <div class='page-grid'>
    <div class='container'>
      <div class='header'>
        <h1>Todos ({{todos.length}})</h1>
      </div>
    </div>
    <div class='container'>
      <add-todo @addTodo='addTodo' />
    </div>
    <div class='container'>
      <div class='list-view'>
        <todo-item
          v-for="todo in todos"
          :key="todo.id"
          :todo='todo'
          @completeItem='completeItem'
          @markIncomplete='markIncomplete'
          @deleteItem='deleteItem'
        />
      </div>
    </div>
  </div>
</template>



<script lang="ts">
import Vue from 'vue';
import AddTodo from './components/AddTodo.vue';
import TodoItem from './components/Todo.vue';
export default {
  components: {
    AddTodo,
    TodoItem
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'Learn Vue',
          description: null,
          completed: false
        },
        {
          id: 2,
          title: 'Create a Sample App',
          description: "Create a sample todo app that holds a list of todo items.",
          completed: true
        },
        {
          id: 3,
          title: 'Deploy Application',
          description: 'Deploy the application on heroku maybe?',
          completed: true
        },
        {
          id: 4,
          title: 'Meet up with Rachel',
          description: 'Dinner at checkers.',
          completed: true
        },
      ]
    }

  },
  methods: {

    addTodo(todo: string, callback: () => void) {
      this.todos.unshift({
        id: 5,
        title: todo,
        description: null,
        completed: false
      });

      callback();
    },

    completeItem(id: number){
      this.todos = this.todos.filter((item) => {
        if(item.id === id)
          item.completed = true;

        return item;
      })
    },

    markIncomplete(id: number){
      this.todos = this.todos.filter((item) => {
        if(item.id === id)
          item.completed = false;

        return item;
      })
    },

    deleteItem(id: number){
      this.todos = this.todos.filter((item) => item.id !== id);
    }
  },

  async created() {
    const results = await window.fetch(`https://jsonplaceholder.typicode.com/todos`);
    const response = await results.json();
    this.todos = response;
  }
};
</script>


<style scoped lang="scss">

.header{
  margin-bottom: 2rem;
}

.container {
  width: 95%;
  max-width: 120rem;
  margin: 0 auto;
}

.list-view{
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 2rem;
}

</style>
