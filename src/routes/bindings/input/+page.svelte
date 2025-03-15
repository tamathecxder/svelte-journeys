<script>
	let name = $state('world');
    let a = $state(1);
	let b = $state(2);
    let yes = $state(false);
    let selected = $state();
    let answer = $state('');

    let questions = $state([
		{
			id: 1,
			text: `Where did you go to school?`
		},
		{
			id: 2,
			text: `What is your mother's name?`
		},
		{
			id: 3,
			text: `What is another personal fact that an attacker could easily find with Google?`
		}
	]);

    function handleSubmit(e) {
        e.preventDefault();

        alert(`Answered question ${selected.id} ${selected.text} with ${answer}`)
    }
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

<!-- Checkbox -->
<label>
	<input type="checkbox" bind:checked={yes} />
	Yes! Send me regular email spam = {yes ? 'Great' : 'Ok, No Problem!'}
</label>

<!-- Select -->
<h2>Insecurity questions</h2>

<form onsubmit={handleSubmit}>
	<select
		bind:value={selected}
		onchange={() => (answer = '')}
	>
		{#each questions as question}
			<option value={question}>
				{question.text}
			</option>
		{/each}
	</select>

	<input bind:value={answer} />

	<button disabled={!answer} type="submit">
		Submit
	</button>
</form>

<p>
	selected question {selected
		? selected.id
		: '[waiting...]'}
</p>