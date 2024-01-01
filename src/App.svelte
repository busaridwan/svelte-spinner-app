<script>
	import Spinner from './Spinner.svelte';
  
	let topic = '';
	let options = [];
	let spinResult = null;
	let backgroundColor = '';
  
	function createSpinner() {
	  // Validate that the user has entered both a topic and at least two options
	  if (topic.trim() === '' || options.length < 2) {
		alert('Please enter a topic and at least two options.');
		return;
	  }
  
	  spinResult = null;
	  backgroundColor = '';
  
	  // You can shuffle the options array here if you want
	}
  
	function handleSpinResult(result, color) {
	  spinResult = result;
	  backgroundColor = color;
	}
  </script>
  
  <main>
	<h1>Create Spinner</h1>
	<label for="topic">Topic:</label>
	<input type="text" bind:value={topic} id="topic" />
  
	<label for="options">Options (comma-separated):</label>
	<input type="text" bind:value={options} id="options" />
  
	<button on:click={createSpinner}>Create Spinner</button>
  
	{spinResult !== null && (
	  <div>
		<h2>Result: {spinResult}</h2>
		<p style="background-color: {backgroundColor}; padding: 10px; border-radius: 5px;">
		  The background color matches the radius the spinner stopped on.
		</p>
	  </div>
	)}
  
	{spinResult === null && <Spinner on:spinResult={handleSpinResult} {options} />}
  </main>
  
  <style>
	main {
	  display: flex;
	  flex-direction: column;
	  align-items: center;
	  justify-content: center;
	  height: 100vh;
	}
  
	h1 {
	  margin-bottom: 20px;
	}
  
	label {
	  margin-top: 10px;
	}
  
	input {
	  margin-bottom: 10px;
	}
  
	button {
	  margin-top: 10px;
	  padding: 10px;
	  cursor: pointer;
	}
  </style>
  