<script lang="ts">
  let todos = [
    { done: false, description: 'Foo' },
    { done: false, description: 'Bar' },
    { done: false, description: 'Baz' },
  ]

  function add() {
    todos = [...todos, { done: false, description: ''}];
  }

  function clear() {
    todos = todos.filter((t) => !t.done);
  }

  $: remaining = todos.filter((t) => !t.done).length;
</script>

<style>
	.done {
		opacity: 0.4;
	}
</style>

{#each todos as todo}
  <div class:done={todo.done}>
    <input type="checkbox" bind:checked={todo.done}>
    <input bind:value={todo.description}>
  </div>
{/each}

<div>{remaining} remaining</div>

<button on:click={add}>Add new</button>
<button on:click={clear}>Clear completed</button>
