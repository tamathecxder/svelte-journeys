<script>
    import { roll } from './utils';

    let promise = $state(roll());
</script>

<a aria-label="dom-events" href="/events/dom-events">Navigate to DOM Events</a>

<button onclick={() => promise = roll()}>
    roll the dice
</button>

{#await promise}
    <p>...rolling</p>
{:then number}
    <p>you rolled a {number}</p>
{:catch error}
    <p style="color: red">{error.message}</p>
{/await}