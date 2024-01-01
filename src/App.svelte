<script>
	import { writable } from 'svelte/store';
	import Spinner from './Spinner.svelte';
  
	let topic = '';
	let options = [];
	let selectedOption = writable('');
	let backgroundColor = 'white'; // Initial background color
  
	function createSpinner() {
	  if (options.length > 0) {
		// Store topic and options (consider using a store for complex scenarios)
		// ...
  
		// Conditionally render the spinner
	  } else {
		// Handle the case where options are missing
	  }
	}
  
	function handleSelectedOption(option) {
	  selectedOption.set(option);
	  backgroundColor = option.color; // Update background color
	}
  </script>
  
  <h1>Spinner App</h1>
  
  <label for="topic">Topic:</label>
  <input type="text" id="topic" bind:value={topic} />
  
  <label for="options">Options:</label>
  <textarea id="options" bind:value={options} />
  
  <button on:click={createSpinner}>Create Spinner</button>
  
  {#if options.length > 0}
	<Spinner options={options} on:selected={handleSelectedOption} />
  {/if}
  
  <p>Selected Option: {selectedOption}</p>
  
  <style>
	/* Add styles for overall app layout and background color */
  </style>
  