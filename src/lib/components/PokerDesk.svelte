<script>
	import { ButtonGroup, GradientButton } from 'flowbite-svelte';
	let cardValues = ['0', '0.5', '1', '2', '3', '5', '8', '13', '20', '40', '❓', '🍵'];
</script>

<ButtonGroup class="gap-4 flex flex-wrap items-center justify-center">
	{#each cardValues as cardValue}
		<GradientButton
			color={cardValue === '5' ? 'purple' : undefined}
			class="w-32 h-48 hover:animate-pulse rounded-lg">{cardValue}</GradientButton
		>
	{/each}
</ButtonGroup>
