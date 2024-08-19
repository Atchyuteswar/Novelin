<script lang="ts">
	import DarkModeSwitch from './DarkModeSwitch.svelte';

	import { page } from '$app/stores';
	import { Download, Menu, X } from 'lucide-svelte';

	let navOpen = false;

	let navItems = ['Home', 'About'];

	// Reactive statement to determine if the current route matches the item
	$: isActive = (item: string) => {
		const routeId = $page.url.pathname;
		navOpen = false;
		if (item == 'Home' && routeId == '/') {
			return true;
		} else {
			return (
				routeId &&
				(`/${item.toLowerCase().split(' ').join('-')}` == routeId || routeId.includes(item))
			);
		}
	};
	//
	const baseClasses = 'block rounded px-3 py-2 md:p-0';
	const activeClasses =
		'bg-yellow-400 text-white md:bg-transparent md:text-yellow-400 md:dark:text-yellow-400';
	const inactiveClasses =
		'text-gray-900 hover:bg-gray-100 dark:border-gray-700 dark:text-white dark:hover:bg-gray-700 dark:hover:text-white md:hover:bg-transparent md:hover:text-yellow-400 md:dark:hover:bg-transparent md:dark:hover:text-yellow-400';
</script>

<!-- 
<nav class="fixed start-0 top-0 z-20 w-full bg-white dark:border-gray-600 dark:bg-gray-900">
	<div class="mx-auto flex max-w-screen-2xl flex-wrap items-center justify-between p-8">
		<div
			class={`w-full items-center justify-between md:flex md:w-auto ${navOpen ? '' : 'hidden'}`}
			id="navbar-sticky"
		>
			<ul
				class="mt-4 flex h-screen flex-col items-center overflow-hidden p-4 text-center font-medium dark:border-gray-700 dark:bg-gray-800 md:mt-0 md:h-auto md:flex-row md:space-x-8 md:border-0 md:bg-white md:p-0 md:dark:bg-gray-900 rtl:space-x-reverse"
			>
				{#each navItems as item}
					<li class="my-1">
						<a
							href={item.toLowerCase().split(' ').join('-')}
							class={isActive(item)
								? 'block rounded bg-yellow-400 px-3 py-2 text-white md:bg-transparent md:p-0 md:text-yellow-400 md:dark:text-yellow-400'
								: 'block rounded px-3 py-2 text-gray-900 hover:bg-gray-100 dark:border-gray-700 dark:text-white dark:hover:bg-gray-700 dark:hover:text-white md:p-0 md:hover:bg-transparent md:hover:text-yellow-400 md:dark:hover:bg-transparent md:dark:hover:text-yellow-400'}
							>{item}</a
						>
					</li>
				{/each}
				<button
					type="button"
					class="bg-dharateal hover:bg-dharateal focus:ring-dharateal dark:bg-dharateal dark:hover:bg-dharateal dark:focus:ring-dharateal mx-auto flex w-full items-center justify-center space-x-2 rounded-lg px-4 py-2 text-center text-sm font-medium text-white focus:outline-none focus:ring-4 md:w-fit"
				>
					Get the App <span class="pl-2"><Download size={18} /></span>
				</button>
			</ul>
		</div>
	
		<a href="/" class="flex items-center space-x-3 rtl:space-x-reverse">
			<span class="size-6">
				<h1>Image</h1>
			</span>
			<span
				class="text-dharateal dark:text-dharateal self-center whitespace-nowrap text-2xl font-semibold"
				>Dhara</span
			>
		</a>
	
		<div class="hidden lg:block">
			<DarkModeSwitch />
		</div>
		<div class="flex space-x-3 md:space-x-0 rtl:space-x-reverse">
			<button
				data-collapse-toggle="navbar-sticky"
				type="button"
				class="order-1 inline-flex h-10 w-10 items-center justify-center rounded-lg p-2 text-sm text-gray-500 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600 md:hidden"
				aria-controls="navbar-sticky"
				aria-expanded="false"
				on:click={() => (navOpen = !navOpen)}
			>
				{#if navOpen}
					<X />
				{:else}
					<Menu />
				{/if}
				<span class="sr-only">Open main menu</span>
			</button>
			<div class="block lg:hidden">
				<DarkModeSwitch />
			</div>
		</div>
	</div>
</nav>
 -->

<nav class="border-gray-200 bg-white dark:bg-gray-900">
	<div class="mx-auto flex max-w-screen-xl flex-wrap items-center justify-between p-4">
		<a href="https://flowbite.com/" class="flex items-center space-x-3 rtl:space-x-reverse">
			<img src="https://flowbite.com/docs/images/logo.svg" class="h-8" alt="Flowbite Logo" />
			<span class="self-center whitespace-nowrap text-2xl font-semibold dark:text-white"
				>Flowbite</span
			>
		</a>
		<button
			data-collapse-toggle="navbar-default"
			type="button"
			class="inline-flex h-10 w-10 items-center justify-center rounded-lg p-2 text-sm text-gray-500 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600 md:hidden"
			aria-controls="navbar-default"
			aria-expanded="false"
		>
			<span class="sr-only">Open main menu</span>
			{#if navOpen}
				<X />
			{:else}
				<Menu />
			{/if}
		</button>
		<div class="hidden w-full md:block md:w-auto" id="navbar-default">
			<ul
				class="mt-4 flex flex-col rounded-lg border border-gray-100 bg-gray-50 p-4 font-medium dark:border-gray-700 dark:bg-gray-800 md:mt-0 md:flex-row md:space-x-8 md:border-0 md:bg-white md:p-0 md:dark:bg-gray-900 rtl:space-x-reverse"
			>
				{#each navItems as item}
					<li class="my-1">
						<a
							href={item.toLowerCase().split(' ').join('-')}
							aria-current={isActive(item) ? 'page' : 'false'}
							class={isActive(item)
								? `${baseClasses} ${activeClasses}`
								: `${baseClasses} ${inactiveClasses}`}>{item}</a
						>
					</li>
				{/each}
			</ul>
		</div>
	</div>
</nav>
