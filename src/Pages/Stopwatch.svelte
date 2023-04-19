<script>
    import { onMount, onDestroy } from 'svelte';
  
    let intervalId;
    let startTime = 0;
    let elapsedTime = 0;
    let isRunning = false;
  
    let miliseconds = 0;
    let seconds = 0;
    let minutes = 0;
    let hours = 0;
  
    function start() {
      startTime = Date.now() - elapsedTime;
      isRunning = true;
      intervalId = setInterval(update, 10);
    }
  
    function stop() {
      clearInterval(intervalId);
      isRunning = false;
    }
  
    function reset() {
      clearInterval(intervalId);
      isRunning = false;
      elapsedTime = 0;
      miliseconds = 0;
      seconds = 0;
      minutes = 0;
      hours = 0;
    }
  
    function update() {
      elapsedTime = Date.now() - startTime;
  
      hours = Math.floor(elapsedTime / 3600000);
      minutes = Math.floor((elapsedTime % 3600000) / 60000);
      seconds = Math.floor((elapsedTime % 60000) / 1000);
      miliseconds = elapsedTime % 1000;
  
    }
  
    onMount(() => {
      start();
    });
  
    onDestroy(() => {
      clearInterval(intervalId);
    });
  
  </script>
  
  <div class="flex justify-center">
    <div class="text-4xl my-4">
      <span class="inline-block">{hours}</span>h
      <span class="inline-block">{minutes}</span>m
      <span class="inline-block">{seconds}</span>s
      <span class="inline-block">{miliseconds}</span>ms
    </div>
  </div>
  
  <div class="flex justify-center space-x-4 mt-6">
    {#if !isRunning}
      <button class="btn" on:click={start}>Start</button>
    {:else}
      <button class="btn" on:click={stop}>Stop</button>
    {/if}
    <button class="btn btn-accent" on:click={reset}>Reset</button>
  </div>
  