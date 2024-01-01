<script>
    import { onMount, tick } from 'svelte';
  
    export let options = [];
  
    let isSpinning = false;
    let selectedOption = '';
  
    function spin() {
      isSpinning = true;
      tick().then(() => {
        const randomIndex = Math.floor(Math.random() * options.length);
        selectedOption = options[randomIndex];
        isSpinning = false;
        emit('selected', selectedOption);
      });
    }
  </script>
  
  <div class="spinner" class:is-spinning={isSpinning}>
    {#each options as option}
      <div class="option" style="background-color: {option.color}">{option.text}</div>
    {/each}
    <button on:click={spin}>Spin</button> </div>
  
  <style>
    /* Styles for spinner elements, animation, and arrow */
  </style>
  