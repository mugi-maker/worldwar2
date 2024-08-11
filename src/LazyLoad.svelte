<script>
    import { onMount, onDestroy } from 'svelte';
    let isVisible = false;
    let observer;
  
    function handleIntersection(entries) {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          isVisible = true;
          observer.unobserve(entry.target);
        }
      });
    }
  
    onMount(() => {
      observer = new IntersectionObserver(handleIntersection, { threshold: 0.1 });
      const element = document.getElementById('lazy-load-element');
      if (element) {
        observer.observe(element);
      }
    });
  
    onDestroy(() => {
      if (observer) {
        observer.disconnect();
      }
    });
  </script>
  
  <div id="lazy-load-element">
    {#if isVisible}
      <slot></slot>
    {/if}
  </div>
  