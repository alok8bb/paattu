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
 width="32" height="32" viewBox="0 0 8.4667 8.4667" xmlns="http://www.w3.org/2000/svg"><path d="m1.27 0a1.1007 1.1007 0 0 0-1.1007 1.1007v6.2653a1.1007 1.1007 0 0 0 1.1007 1.1007h1.1853a1.1007 1.1007 0 0 0 1.1007-1.1007v-6.2653a1.1007 1.1007 0 0 0-1.1007-1.1007zm4.7413 0a1.1007 1.1007 0 0 0-1.1007 1.1007v6.2653a1.1007 1.1007 0 0 0 1.1007 1.1007h1.1853a1.1007 1.1007 0 0 0 1.1007-1.1007v-6.2653a1.1007 1.1007 0 0 0-1.1007-1.1007z" fill="currentColor" stroke-width=".33867"/></svg>


