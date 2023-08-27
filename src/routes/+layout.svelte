<script>
	import '../app.postcss';
	import { page } from '$app/stores';
	import { Navbar, NavBrand, NavLi, NavUl, NavHamburger, DarkMode } from 'flowbite-svelte';
	import { Icon } from 'flowbite-svelte-icons';
	import { goto } from '$app/navigation';
	$: activeUrl = $page.url.pathname;
	const start = () => {
		// Generate a game id
		const id = 18;
		goto(`/game/${id}`);
	};
</script>

<Navbar let:hidden let:toggle color="none">
	<div class="flex">
		<DarkMode />
		<NavBrand href="/">
			<span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white uppercase"
				>Scrum Poker</span
			>
		</NavBrand>
	</div>
	<NavHamburger on:click={toggle} />
	<NavUl {activeUrl} {hidden}>
		<NavLi class="cursor-pointer flex gap-x-2" on:click={start}
			><Icon name="plus-solid" />start</NavLi
		>
		<NavLi href="https://naveenkumar.vercel.app/" target="_blank" class="flex gap-x-2"
			><Icon name="code-solid" />author</NavLi
		>
	</NavUl>
</Navbar>
<div class="flex flex-col justify-center items-center">
	<slot />
</div>
