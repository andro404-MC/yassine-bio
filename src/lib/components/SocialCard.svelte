<script>
  import { onMount } from "svelte";
  export let title;
  export let paragraph;
  export let bg;
  export let link;
  export let imgLink;
  import { fade } from "svelte/transition";
  let loaded = false
  onMount(() => {
    setTimeout(() => {
      loaded = true;
    }, 0.3);
  });
</script>
{#if loaded}
<a target="_blank" in:fade={{duration:600}} href="{link}">
  <div class="card bg-base-300 shadow-xl">
    <div class="card-body p-5">
      <h2 class="card-title">{title}</h2>
      <p>{paragraph}</p>
    </div>
    <figure style="background:{bg};" class="p-2 sm:p-10">
      <img height="48" width="144" src="{imgLink}" alt="logo" />
    </figure>
  </div>
</a>

{/if}
