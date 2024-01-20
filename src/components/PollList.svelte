<script>
  import PollDetails from "./PollDetails.svelte";
  import PollStore from "../stores/PollStore.js";
  import { fade, scale, slide } from "svelte/transition";
  import { flip } from "svelte/animate";
  //   import { onDestroy, onMount } from "svelte";

  //   const unsub = PollStore.subscribe((data) => {
  //     polls = data;
  //   });

  //   onDestroy(() => {
  //     unsub();
  //   });
</script>

<div class="poll-list">
  {#each $PollStore as poll (poll.id)}
    <div in:fade out:scale|local animate:flip={{ duration: 500 }}>
      <PollDetails on:vote {poll} />
    </div>
  {/each}
</div>

<style>
  .poll-list {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
  }

  @media (max-width: 600px) {
    .poll-list {
      grid-template-columns: 1fr;
      grid-gap: 30px;
    }
  }
</style>
