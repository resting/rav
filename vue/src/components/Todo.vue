<template>
  <div class="todo">
    <h1>New TODO</h1>
    <label for="">New todo:</label>
    <form v-on:submit.prevent="onSubmit">
      <input type="text" name="desc"><input type="submit" value="Add">
    </form>

    <ul class="new-todos">
      <li v-for="todo in newTodos">
        {{todo.desc}}
        <button v-on:click="onDoing" v-bind:data-id="todo.id">Doing</button>
        <button v-on:click="onDone" v-bind:data-id="todo.id">Done</button>
      </li>
    </ul>
  </div>
</template>
<script>
  let id = 0;
  export default {
    name: 'todo',
    props: ['todos'],
    methods: {
      onSubmit(e) {
        this.todos.push({
          id: id += 1,
          desc: e.target.desc.value,
          status: 'new',
        });
        this.$emit('new');
      },
      onDoing(e) {
        const tid = e.target.dataset.id - 1;
        this.todos[tid].status = 'doing';
      },
      onDone(e) {
        console.log(e.target);
      },
    },
    computed: {
      newTodos() {
        return this.todos.filter(t => t.status === 'new');
      },
    },
  };
</script>