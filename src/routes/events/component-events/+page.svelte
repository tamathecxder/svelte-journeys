<script>
	import Stepper from "./Stepper.svelte";

    let value = $state(0);
</script>

<a aria-label="input" href="/bindings/input">Navigate to input binding</a>

<p>The current value is {value}</p>

<Stepper
    increment={() => value += 1}
    decrement={() => value -= 1}
 />