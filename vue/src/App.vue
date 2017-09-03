<template>
  <div id="app">
    <div class="grid">
      <Todo v-bind:todos="todos" v-on:new="newTodo"/>
      <Doing v-bind:todos="todos"/>
      <Done v-bind:todos="todos"/>
    </div>
  </div>
</template>

<script>
  import Todo from './components/Todo';
  import Doing from './components/Doing';
  import Done from './components/Done';

  export default {
    name: 'app',
    data() {
      return {
        todos: [
          {
              id: 1,
              desc: 'aa',
              status: 'new',
          },
          {
              id: 2,
              desc: 'bb',
              status: 'new',
          },
        ],
      };
    },
    components: {
      Todo,
      Doing,
      Done,
    },
    methods: {
      newTodo() {
        console.log(this.todos);
      },
    },
  };
</script>

<style>
  .grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 1em;
    height: 100vh;
  }

  .todo {
    background: #aaa;
  }

  .doing {
    background: #ccc;
  }

  .done {
    background: #eee;
  }

</style>
