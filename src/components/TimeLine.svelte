<script>
import { setInterval } from "timers";

  import Card from "./Card.svelte";
  export let posts = [];
  
</script>

<!-- TimeLine.svelte -->


<style>
  .TimeLine {
    padding: 4em 0 0 0;
  }
</style>

<div class="TimeLine">
  <div class="TimerLine-contai">
    {#each posts as post}
      <Card {...post}/>
  
    {:else}
      <p>
        loading...
      </p>
    {/each}

  </div>
</div>