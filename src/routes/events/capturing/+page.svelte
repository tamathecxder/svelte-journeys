<div onkeydowncapture={(e) => alert(`<div> ${e.key}`)} role="presentation">
    <a aria-label="component-events" href="/events/component-events">Navigate to capturing component events</a>
    
	<input onkeydowncapture={(e) => alert(`<input> ${e.key}`)} />
</div>
