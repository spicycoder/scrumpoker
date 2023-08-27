<script lang="ts">
	import { ButtonGroup, Card, GradientButton } from 'flowbite-svelte';
	const playerValues: { name: string; value: string | null }[] = [
		{
			name: 'Peter Parker',
			value: '5'
		},
		{
			name: 'Bruce Wayne',
			value: '13'
		},
		{
			name: 'Tony Stark',
			value: '3'
		},
		{
			name: 'Clark Kent',
			value: '❓'
		},
		{
			name: 'Wanda Maximoff',
			value: '5'
		},
		{
			name: 'Diana Prince',
			value: null
		}
	].sort((a, b) => (a.name > b.name ? 1 : a.name < b.name ? -1 : 0));
</script>

<div class="gap-4 flex flex-wrap items-center justify-center text-center">
	{#each playerValues as playerValue}
		{#if playerValue.value}
			<Card
				class="w-32 h-48 justify-between hover:animate-pulse"
				color="indigo"
				border={false}
				shadow={true}
				rounded={true}
				padding="xl"
				><p>{playerValue.name}</p>
				<p>{playerValue.value}</p>
			</Card>
		{:else}
			<Card
				class="w-32 h-48 justify-between hover:animate-pulse"
				color="red"
				border={false}
				shadow={true}
				rounded={true}
				padding="xl"
				><p>{playerValue.name}</p>
			</Card>
		{/if}
	{/each}
</div>
