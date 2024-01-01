<script>
    import { onMount, createEventDispatcher } from 'svelte';
  
    export let options;
  
    const dispatch = createEventDispatcher();
  
    let spinResult = null;
    let backgroundColor = '';
  
    onMount(() => {
      const spinner = document.getElementById('spinner');
      spinner.style.setProperty('--total-segments', options.length);
    });
  
    function spin() {
      const randomIndex = Math.floor(Math.random() * options.length);
      const selectedOption = options[randomIndex];
      const rotation = (360 / options.length) * randomIndex;
      spinResult = selectedOption;
      backgroundColor = getColor(randomIndex);
      dispatch('spinResult', spinResult, backgroundColor);
      rotateSpinner(rotation);
    }
  
    function rotateSpinner(degrees) {
      const spinner = document.getElementById('spinner');
      spinner.style.transition = 'transform 2s ease-in-out';
      spinner.style.transform = `rotate(${degrees}deg)`;
      setTimeout(() => {
        spinner.style.transition = 'none';
        spinner.style.transform = 'rotate(0deg)';
      }, 2000);
    }
  
    function getColor(index) {
      // You can customize the color logic based on the index
      return index % 2 === 0 ? 'lightblue' : 'lightgreen';
    }
  </script>
  
  <div id="spinner" on:click={spin}>
    {#each options as option, index (option)}
      <div
        class="segment"
        style={`transform: rotate(${(360 / options.length) * index}deg) translate(100px) rotate(-${(360 / options.length) * index}deg);`}
      >
        {option}
      </div>
    {/each}
  </div>
  
  <style>
    #spinner {
      width: 200px;
      height: 200px;
      position: relative;
      margin-top: 20px;
    }
  
    .segment {
      position: absolute;
      top: 50%;
      left: 50%;
      width: 50px;
      height: 50px;
      background-color: transparent;
      border: 1px solid #000;
      text-align: center;
      line-height: 50px;
      transform-origin: center bottom;
    }
  </style>
  