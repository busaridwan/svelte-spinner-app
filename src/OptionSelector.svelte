<script>
    import { createEventDispatcher } from 'svelte';
  
    const dispatch = createEventDispatcher();
  
    const options = ['Option 1', 'Option 2', 'Option 3', 'Option 4'];
  
    function selectOption(option) {
      dispatch('optionSelected', option);
    }
  </script>
  
  <div>
    <h2>Select an option:</h2>
    <ul>
      {#each options as option (option)}
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <li on:click={() => selectOption(option)}>{option}</li>
      {/each}
    </ul>
  </div>
  
  <style>
    ul {
      list-style: none;
      padding: 0;
    }
  
    li {
      cursor: pointer;
      margin: 5px;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
  </style>
  