<script>
	import { fade } from "svelte/transition";

    let visible = $state(true);
</script>

<label>
    <input type="checkbox" bind:checked={visible}>
    Visible 
</label>

{#if visible}
    <p transition:fade>
        Fades in and out
    </p>
{/if}