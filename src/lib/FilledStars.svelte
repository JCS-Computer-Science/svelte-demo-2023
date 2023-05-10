<script>
	export let score;
	export let max = 5;
	let fills = [];
	for (let i = 0; i < max; i++) {
		if (score - i > 1) {
			fills.push(1);
		} else if (score - i > 0) {
			fills.push(score - i);
		} else {
			fills.push(0);
		}
	}
</script>

<div>
	{#each fills as val, i (i)}
		<svg height="24" viewBox="0 0 24 24" width="24">
			<defs>
				<linearGradient id="grad-{val}">
					<stop offset="{val * 100}%" stop-color="orange" />
					<stop offset="{val * 100}%" stop-color="white" />
				</linearGradient>
			</defs>

			<path
				fill="url(#grad-{val})"
				stroke="black"
				stroke-width="0.5"
				d="M12 17.27L18.18 21l-1.64-7.03L22 9.24l-7.19-.61L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21z"
			/>
		</svg>
	{/each}
</div>
