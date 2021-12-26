<script>
    // Props
    // 외부와의 통로 개념
    export let fruits
    export let reverse
    export let slice

    let computedFruites = []
    let name = ''

    if(reverse) {
        computedFruites = [...fruits].reverse()
        name = 'reverse'
    } else if (slice) {
        computedFruites = [...fruits].slice(...slice.split(','))
        name = `slice ${slice}`

    } else {
        computedFruites = [...fruits]

    }
</script>

<h2>
	Fruits {name}
</h2>
<ul>
	{#each computedFruites as fruit}
	<li>{fruit}</li>
	{/each}
</ul>