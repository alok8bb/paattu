<script>
  import { paused } from "$lib/store";

  function playtoggle() {
    $paused = !$paused;
  }
</script>

<svg 
class="glow"
on:click={playtoggle}
on:keypress={playtoggle}
width="32" height="32" viewBox="0 0 8.4667 8.4667" xmlns="http://www.w3.org/2000/svg"><path d="m2.1966 0.16188c-0.82367-0.46563-1.8431 0.12875-1.8431 1.0745v5.9939c0 0.94607 1.0202 1.5405 1.8435 1.0741l5.2902-2.9977c0.83496-0.47304 0.8346-1.6759 0-2.1486l-5.2909-2.9963z" fill="currentColor" stroke-width=".35275"/></svg>

