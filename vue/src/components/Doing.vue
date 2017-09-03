<template>
  <div class="doing">
    <h1>Doing</h1>

    <ul class="doing-todos">
      <li v-for="todo in doingTodos">
        {{todo.desc}}
        <button v-on:click="onDone" v-bind:data-id="todo.id">Done</button>
      </li>
    </ul>
  </div>
</template>
<script>
  export default {
    name: 'doing',
    props: ['todos'],
    computed: {
      doingTodos() {
        return this.todos.filter(t => t.status === 'doing');
      },
    },
    updated() {
      console.log(this.todos);
    },
  };
</script>