<script>
	import { fly } from "svelte/transition";

    let visible = $state(true);
</script>

<label>
    <input type="checkbox" bind:checked={visible}>
    Visible 
</label>

{#if visible}
    <p transition:fly={{ y: 200, duration: 2000 }}>
        Fades in and out
    </p>
{/if}