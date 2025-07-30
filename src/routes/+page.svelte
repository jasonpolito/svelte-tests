<script lang="ts">
	const total = 100;
	let spent: number = $state(0);
	let btn = $state({
		padding: {
			y: 12,
			x: 18
		},
		color: {
			text: '#ffffff',
			background: '#1ca0ba'
		}
	});
	let tailwindClasses = $derived.by(() => {
		return `text-center rounded px-${btn.padding.x} py-${btn.padding.y} bg-[${btn.color.background}]`;
	});

	let tailwindOutput = $derived.by(() => {
		return `<button class="text-center rounded px-[${btn.padding.x}px] py-[${btn.padding.y}px] bg-[${btn.color.background}] text-[${btn.color.text}]">Howdy Partner!</button>`;
	});

	let inlineStyles = $derived.by(() => {
		return `color: ${btn.color.text}; padding: ${btn.padding.y}px ${btn.padding.x}px; background: ${btn.color.background};`;
	});

	function updateLeft(left: number) {
		spent = total - left;
	}

	console.log('spent', spent);

	export const prerender = true;
</script>

<div class="p-8">
	<div class="flex min-h-[50vh] items-center justify-center rounded bg-slate-50 p-16 shadow-inner">
		<button style={inlineStyles} class={tailwindClasses}> Howdy Partner! </button>
	</div>
</div>

<input type="range" bind:value={btn.padding.y} />
<input type="number" bind:value={btn.padding.y} />
<input type="range" bind:value={btn.padding.x} />
<input type="number" bind:value={btn.padding.x} />
<input type="color" bind:value={btn.color.text} />
<input type="color" bind:value={btn.color.background} />

<pre>
    {tailwindOutput}
</pre>

<style>
	* {
		position: relative;
	}
</style>
