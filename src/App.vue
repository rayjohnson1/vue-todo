<template>
  <div class='page-grid'>
    <div class='header'>
      <h1>Todos</h1>
    </div>
    <div class='container'>
      <div class='list-view'>
        <figure v-for="todo in todos" :key="todo.id" class='todo-item'>
          <i v-if="todo.completed" class="fas fa-check-circle todo-item__status todo-item__status--complete"></i>
          <i v-else class="far fa-check-circle todo-item__status todo-item__status--incomplete"></i>
          <div>
            <h5>{{ todo.title }}</h5>
            <p v-if="todo.description">{{ todo.description }}</p>
          </div>
        </figure>
      </div>
    </div>
  </div>
</template>



<script lang="ts">
import Vue from 'vue';
export default {
  components: {
    
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

  }
};
</script>


<style lang="scss">

  .page-grid {
    display: grid;
    grid-template-rows: 12rem;
  }

  .header {
    background: white;
    box-shadow: 0 1rem 1rem rgba(black, .1);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .container{
    width: 95%;
    max-width: 120rem;
    margin: 0 auto;
  }

  .list-view {
    padding-top: 3rem;
  }

  .todo-item{
    margin-bottom: 3rem;
    padding: 2rem;
    background: white;
    box-shadow: 0 .5rem 1.2rem rgba(black, .1);
    border: 1px solid rgb(221, 221, 221);
    display: flex;
    align-items: center;

    &__status{
      font-size: 2rem;
      margin-right: 2rem;

      &--complete{
        color: green;
      }

      &--incomplete{
        color: red;
      }
    }
  }

</style>
