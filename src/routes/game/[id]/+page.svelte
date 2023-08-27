<script lang="ts">
	import { goto } from '$app/navigation';
	import { page } from '$app/stores';
	import DisplayDesk from '$lib/components/DisplayDesk.svelte';
	import PokerDesk from '$lib/components/PokerDesk.svelte';
	import {
		Button,
		Card,
		CardPlaceholder,
		FloatingLabelInput,
		Heading,
		Hr,
		ListPlaceholder,
		Modal
	} from 'flowbite-svelte';
	import { onMount } from 'svelte';
	let collectName = false;
	let name: string = '';
	let nameInput: string = '';
	let id: string = '';

	onMount(() => {
		id = $page.params.id;
		name = localStorage.getItem('name') ?? '';
		collectName = !name;

		if (id !== '18') {
			alert('Invalid game id, redirecting to home page');
			goto(`/`);
		}
	});
</script>

{#if !name}
	<Card title="Refersh to enter your name" class="my-4">
		<Heading tag="h4" class="text-center my-2">Required user name</Heading>
		<p>
			<a href={`/game/${id}`} target="_self"><span class="underline">Refresh</span></a> to enter your
			name to join the game
		</p>
		<p class="text-center">
			Or, visit <a href="/"><span class="underline">Home</span></a> to start a new game
		</p>
	</Card>
	<div class="flex flex-col md:flex-row gap-4">
		<ListPlaceholder />
		<CardPlaceholder />
	</div>
{:else}
	<DisplayDesk />
	<Hr classHr="w-48 h-1 mx-auto my-4 rounded md:my-10" />
	<PokerDesk />
{/if}

<Modal title="Join the game" size="xs" outsideclose={false} open={collectName} autoclose>
	<FloatingLabelInput type="text" bind:value={nameInput} label="name" />
	<svelte:fragment slot="footer">
		<Button
			disabled={!nameInput}
			on:click={() => {
				name = nameInput;
				localStorage.setItem('name', name ?? '');
			}}>Submit</Button
		>
	</svelte:fragment>
</Modal>
