<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/oeil.svg';
	import oeilBlanc from '$lib/assets/oeil-blanc.svg';
	import menu from '$lib/assets/menu.svg';

	let { data, children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<header class="fixed w-full">
	<div class=" flex items-center px-16 py-6 font-fledora text-white">
		<div class="flex-1">
			<img
				src={oeilBlanc}
				alt="Logo"
				class="inset-0 w-15 h-15 min-h-0 p-2 bg-theme-orange object-contain"
			/>
		</div>
		<div class="flex-1 flex justify-center">
			<span class="uppercase pb-2 pt-3 px-8 bg-theme-orange text-center text-3xl leading-[80%]"
				>Metal <br /> access</span
			>
		</div>
		<div class="flex-1 flex justify-end items-center gap-4">
			<span class="uppercase text-xl leading-[80%]">Menu</span>
			<button class="cursor-pointer p-4 border border-theme-lightOrange bg-theme-orange">
				<img src={menu} alt="Menu" class="w-4.5 h-full object-contain" />
			</button>
		</div>
	</div>
</header>
{@render children()}
