<script lang="ts">
  import App from './example/App.svelte';
  import Apps from './examples/Apps.svelte';
  import Gays from './gay/gays.svelte';
  import LazyLoad from './LazyLoad.svelte';

  import { onMount } from 'svelte';
  let showDiv = false;

  onMount(() => {
    setTimeout(() => {
      showDiv = true;
    }, 3000); // 3000 milliseconds = 3 seconds
  });

  let secondsLeft = 3600; // Set the initial countdown time in seconds (e.g., 1 hour)

  function updateCountdown() {
    const interval = setInterval(() => {
      if (secondsLeft > 0) {
        secondsLeft -= 1;
      } else {
        clearInterval(interval); // Stop the countdown when it reaches zero
      }
    }, 1000); // Update every second
  }


  


</script>
<h1>hello</h1>

<!-- div -->
<div role="alert" class="alert alert-info">
  <svg
    xmlns="http://www.w3.org/2000/svg"
    fill="none"
    viewBox="0 0 24 24"
    class="h-6 w-6 shrink-0 stroke-current">
    <path
      stroke-linecap="round"
      stroke-linejoin="round"
      stroke-width="2"
      d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
  </svg>
  <span>New software update available.</span>
</div>

<!-- div -->





{#if !showDiv}

  <div class="loading-screen">
    Loading...
  </div>
{/if}

{#if showDiv}
  <div class="main">
    <div class="screen">
      <LazyLoad>
        <div class ="artboard "><App /></div><br>
        <Apps /><br>
        <Gays />
      </LazyLoad>
    </div>
  </div>

{/if}

<style>
  :global(body, html) {
    margin: 0;
  }

  .button-bar {
    align-items: center;
    display: flex;
  }

  .screen {
    margin-left: 10%;
    margin-right: 10%;
    align-items: center;
    position: absolute;
    height: 10px;
    width: 80%;
  }

  .btn {
    margin-left: 10px;
  }

  .main {
    align-items: center;
  }
   .artboard {
     width: 100%;
     height: 100px;
   
   }
  .loading-screen {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: rgba(0, 0, 0, 0.5);
    color: white;
    font-size: 1.5em;
    z-index: 1000;
  }

  .carousel{
    display: flex;
    height: 70%;
  }
  .carousel-item{
    height: 100%;
  }
</style>
