<!-- TodoList.svelte -->
<script>
  let tasks = [];
  let newTask = '';

  function addTask() {
    if (newTask !== '') {
      tasks = [...tasks, { id: Date.now(), text: newTask, done: false }];
      newTask = '';
    }
  }

  function deleteTask(id) {
    tasks = tasks.filter(task => task.id !== id);
  }

  function toggleTaskDone(id) {
    tasks = tasks.map(task => {
      if (task.id === id) {
        return { ...task, done: !task.done };
      }
      return task;
    });
  }
</script>
<div class="form-control my-4">
  <label class="input-group ">
    <input type="text"  class="input input-bordered w-full px-4 py-2 " placeholder="Add a task" bind:value={newTask} on:keyup={({ key }) => key === 'Enter' && addTask()} />
    <button class="btn-primary px-4 py-2 rounded " on:click={addTask}>
      Add
    </button>
  </label>
</div>


{#if tasks.length === 0}
  <p>No tasks yet.</p>
{:else}
  <ul class="list-disc list-inside">
    {#each tasks as task (task.id)}
      <li class="flex justify-between items-center mb-2" id="{task.id}">
        <label class="flex items-center cursor-pointer">
          <input type="checkbox" class="form-checkbox h-5 w-5 checkbox checkbox-primary" checked={task.done} on:change={() => toggleTaskDone(task.id)} />
          <span class="ml-2">{task.text}</span>
        </label>
        <button class="btn btn-accent" on:click={() => deleteTask(task.id)}>
          Delete
        </button>
      </li>
    {/each}
  </ul>
{/if}
