<script>
	let name = $state('world');
    let a = $state(1);
	let b = $state(2);
</script>

<!-- Input Text -->
<input bind:value={name} />

<h1>Hello {name}!</h1>

<!-- Input Number -->
<label>
	<input type="number" bind:value={a} min="0" max="10" />
	<input type="range" bind:value={a} min="0" max="10" />
</label>

<label>
	<input type="number" bind:value={b} min="0" max="10" />
	<input type="range" bind:value={b} min="0" max="10" />
</label>

<p>{a} + {b} = {a + b}</p>

