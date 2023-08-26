<script lang="ts">
	import { Button, Card, FloatingLabelInput, GradientButton } from 'flowbite-svelte';
	export let newSession = true;
	let name: string = '';
	let id: number | null = 18;
	$: enabled = id && name;
</script>

<Card class="gap-y-4">
	<FloatingLabelInput type="number" label="Id" bind:value={id} disabled={newSession} />
	<FloatingLabelInput type="text" label="Name" bind:value={name} />
	<GradientButton
		pill
		disabled={!enabled}
		on:click={() => {
			console.log(id, name);
		}}>Submit</GradientButton
	>
</Card>
