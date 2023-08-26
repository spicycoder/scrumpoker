<script>
	import '../app.postcss';
	import { page } from '$app/stores';
	import { blur } from 'svelte/transition';
	import { Navbar, NavBrand, NavLi, NavUl, NavHamburger, DarkMode, Popover } from 'flowbite-svelte';
	$: activeUrl = $page.url.pathname;
</script>

<Navbar let:hidden let:toggle>
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
		<NavLi href="/start">Start</NavLi>
		<Popover arrow={false} placement="bottom" title="Start" transition={blur}
			>Start a new poker session</Popover
		>
		<NavLi href="/join">Join</NavLi>
		<Popover arrow={false} placement="bottom" title="Join" transition={blur}
			>Join an existing poker session</Popover
		>
		<NavLi href="https://naveenkumar.vercel.app/" target="_blank">author</NavLi>
	</NavUl>
</Navbar>

<div class="flex flex-col justify-center items-center">
	<slot />
</div>
