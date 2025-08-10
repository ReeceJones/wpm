<script lang="ts">
	let {
		active,
		currentInput,
		word,
		scrollToWord
	}: { active: boolean; currentInput: string; word: string; scrollToWord?: boolean } = $props();

	$effect(() => {
		if (scrollToWord) {
			const element = document.getElementById(word);
			if (element) {
				element.scrollIntoView({ behavior: 'smooth' });
			}
		}
	});
</script>

<p>
	{#if active}
		{#if word.startsWith(currentInput)}
			<span class="bg-success text-lg font-extrabold text-white" id={word}
				>{word.slice(0, currentInput.length)}</span
			><span class="bg-base-300 text-lg font-extrabold text-white"
				>{word.slice(currentInput.length)}</span
			>
		{:else}
			<span class="bg-error text-lg font-extrabold text-white">{word}</span>
		{/if}
	{:else}
		<span class="text-lg font-bold" id={word}>{word}</span>
	{/if}
</p>
