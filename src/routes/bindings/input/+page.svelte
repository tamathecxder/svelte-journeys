<script lang="ts">    
	let name = $state('world');
    let a = $state(1);
	let b = $state(2);
    let yes = $state(false);
    let selected: any = $state();
    let answer = $state('');
    let scoops = $state(1);
	let flavours: any = $state([]);
    let value = $state('Some words are *italic*')

	const formatter = new Intl.ListFormat('en', { style: 'long', type: 'conjunction' });

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

    function handleSubmit(e: any) {
        e.preventDefault();

        alert(`Answered question ${selected.id} ${selected.text} with ${answer}`)
    }
</script>

<a aria-label="class" href="/classes/class-attribute">Navigate to class attribute</a>

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

<!-- Group Inputs -->
<h2>Size</h2>

{#each [1, 2, 3] as number}
	<label>
		<input
			type="radio"
			name="scoops"
			value={number}
            bind:group={scoops}
		/>

		{number} {number === 1 ? 'scoop' : 'scoops'}
	</label>
{/each}

<h2>Flavours</h2>

{#each ['cookies and cream', 'mint choc chip', 'raspberry ripple'] as flavour}
	<label>
		<input
			type="checkbox"
			name="flavours"
			value={flavour}
            bind:group={flavours}
		/>

		{flavour}
	</label>
{/each}

{#if flavours.length === 0}
	<p>Please select at least one flavour</p>
{:else if flavours.length > scoops}
	<p>Can't order more flavours than scoops!</p>
{:else}
	<p>
		You ordered {scoops} {scoops === 1 ? 'scoop' : 'scoops'}
		of {formatter.format(flavours)}
	</p>
{/if}

<!-- Select Multiple -->
<select multiple bind:value={flavours}>
    {#each ['cookies and cream', 'mint', 'mengkudu'] as flavour}
        <option>{flavour}</option>
    {/each}
</select>

<!-- Textarea -->
<div class="grid">
	input
	<textarea bind:value></textarea>

	output
	<div>{@html value}</div>
</div>

<style>
	.grid {
		display: grid;
		grid-template-columns: 5em 1fr;
		grid-template-rows: 1fr 1fr;
		grid-gap: 1em;
		height: 100%;
	}

	textarea {
		flex: 1;
		resize: none;
	}
</style>

