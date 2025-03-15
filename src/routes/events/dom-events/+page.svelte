<script lang="ts">
	let m = $state({ x: 0, y: 0 });
</script>


<div onpointermove={(event: any) => {
    m.x = event.clientX;
    m.y = event.clientY;
}}>
<a aria-label="capturing" href="/events/capturing">Navigate to capturing event</a>
	The pointer is at {Math.round(m.x)} x {Math.round(m.y)}
</div>

<style>
	div {
		position: fixed;
		left: 0;
		top: 0;
		width: 100%;
		height: 100%;
		padding: 1rem;
	}
</style>
