<script>
  import TodoList from './Pages/TodoList.svelte';
  import Calculator from './Pages/Calculator.svelte';
  import Stopwatch from './Pages/Stopwatch.svelte';
  import Generator from './Pages/Generator.svelte';
  let activeTab = 'todoList';

  function setActiveTab(tab) {
    activeTab = tab;
  }
</script>

<div class="fixed inset-0 flex items-center justify-center">
  <div class="">
    <div class="tabs">
      <button class="tab tab-bordered" class:active={activeTab === 'todoList'} class:tab-active={activeTab === 'todoList'} on:click={() => setActiveTab('todoList')}>
        Todo List
      </button>
      <button class="tab tab-bordered" class:active={activeTab === 'calculator'} class:tab-active={activeTab === 'calculator'} on:click={() => setActiveTab('calculator')}>
        Calculator
      </button>
      <button class="tab tab-bordered" class:active={activeTab === 'stopwatch'} class:tab-active={activeTab === 'stopwatch'} on:click={() => setActiveTab('stopwatch')}>
        Stopwatch
      </button>
      <button class="tab tab-bordered" class:active={activeTab === 'generator'} class:tab-active={activeTab === 'generator'} on:click={() => setActiveTab('generator')}>
        Generator
      </button>
    </div>
    
    <div class="card w-full">
      {#if activeTab === 'todoList'}
        <TodoList />
      {:else if activeTab === 'calculator'}
        <Calculator />
      {:else if activeTab === 'stopwatch'}
        <Stopwatch />
        {:else if activeTab === 'generator'}
        <Generator />
      {/if}
    </div>
  </div>
</div>
