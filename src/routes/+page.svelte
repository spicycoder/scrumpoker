<script lang="ts">
	import { goto } from '$app/navigation';
	import { blur } from 'svelte/transition';
	import { Blockquote, ButtonGroup, Card, GradientButton, Popover } from 'flowbite-svelte';
	import { Icon } from 'flowbite-svelte-icons';
</script>

<Card class="mt-4" size="lg">
	<div class="flex flex-col items-center justify-center">
		<h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white text-center">
			Scrum Poker
		</h5>
		<Blockquote size="lg">
			<Icon name="quote-solid" class="w-10 h-10 text-gray-400 dark:text-gray-600" />
			Scrum Poker is a consensus-based estimating technique used in agile software development to help
			teams estimate the amount of work required to complete tasks in the product backlog. This online
			web application allows you to play Scrum Poker with your team members in real time. Simply create
			a game, add the tasks, and start playing. The application will track the estimates of your team
			members and help you reach a consensus. Scrum Poker is a great way to improve the accuracy of your
			estimates and make better decisions about your project.
		</Blockquote>
		<ButtonGroup class="mt-4">
			<GradientButton pill class="w-24" on:click={() => goto('/start')}>Start</GradientButton>
			<Popover title="Start" arrow={false} placement="bottom" transition={blur}
				>Start a new poker session</Popover
			>
			<GradientButton pill class="w-24" on:click={() => goto('join')}>Join</GradientButton>
			<Popover title="Join" arrow={false} placement="bottom" transition={blur}
				>Join an existing poker session</Popover
			>
		</ButtonGroup>
	</div>
</Card>
