<script lang="ts">
	import DarkModeSwitch from './DarkModeSwitch.svelte';

	import { page } from '$app/stores';
	import { Download, Menu, X } from 'lucide-svelte';

	let navOpen = false;

	let navItems = ['Home', 'Books'];

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
	function getHref(text: string) {
		if (text.toLowerCase() === 'home') {
			return '/';
		} else {
			return text.toLowerCase().split(' ').join('-');
		}
	}

	//
	const baseClasses = 'block rounded px-3 py-2 md:p-0';
	const activeClasses =
		'bg-yellow-400 text-white dark:text-black md:bg-transparent md:text-yellow-400 md:dark:text-yellow-400';
	const inactiveClasses =
		'text-gray-900 hover:bg-gray-100 dark:border-gray-700 dark:text-white dark:hover:bg-gray-700 dark:hover:text-white md:hover:bg-transparent md:hover:text-yellow-400 md:dark:hover:bg-transparent md:dark:hover:text-yellow-400';
</script>

<nav class="border-gray-200 bg-white dark:bg-gray-900">
	<div class="mx-auto flex max-w-screen-xl flex-wrap items-center justify-between p-4 px-14">
		<div
			class:hidden={!navOpen}
			class="order-last w-full md:order-none md:block md:w-auto"
			id="navbar-default"
		>
			<ul
				class="mt-4 flex flex-col rounded-lg border border-gray-100 bg-gray-50 p-4 font-medium dark:border-gray-700 dark:bg-gray-800 md:mt-0 md:flex-row md:space-x-8 md:border-0 md:bg-white md:p-0 md:dark:bg-gray-900 rtl:space-x-reverse"
			>
				{#each navItems as item}
					<li class="my-1">
						<a
							href={getHref(item)}
							aria-current={isActive(item) ? 'page' : 'false'}
							class={isActive(item)
								? `${baseClasses} ${activeClasses}`
								: `${baseClasses} ${inactiveClasses}`}>{item}</a
						>
					</li>
				{/each}
			</ul>
		</div>
		<!--  -->
		<a href="/" class="flex items-center space-x-3 rtl:space-x-reverse">
			<!-- Change this later -->
			<img src="https://flowbite.com/docs/images/logo.svg" class="h-8" alt="Novelin Logo" />
			<span class="self-center whitespace-nowrap text-2xl font-semibold dark:text-white"
				>Novelin</span
			>
		</a>
		<!--  -->
		<div
			class:hidden={!navOpen}
			class="order-last w-full md:order-none md:block md:w-auto"
			id="navbar-secondary"
		>
			<ul
				class="mt-4 flex flex-col rounded-lg border border-gray-100 bg-gray-50 p-4 font-medium dark:border-gray-700 dark:bg-gray-800 md:mt-0 md:flex-row md:space-x-8 md:border-0 md:bg-white md:p-0 md:dark:bg-gray-900 rtl:space-x-reverse"
			>
				{#each ['Learn More'] as item}
					<li class="my-1">
						<a
							href={getHref(item)}
							aria-current={isActive(item) ? 'page' : 'false'}
							class={isActive(item)
								? `${baseClasses} ${activeClasses}`
								: `${baseClasses} ${inactiveClasses}`}>{item}</a
						>
					</li>
				{/each}
			</ul>
		</div>
		<!--  -->
		<span class="space-x-5">
			<DarkModeSwitch />
			<button
				data-collapse-toggle="navbar-default"
				type="button"
				class="inline-flex h-10 w-10 items-center justify-center rounded-lg p-2 text-sm text-gray-500 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600 md:hidden"
				aria-controls="navbar-default"
				aria-expanded="false"
				on:click={() => {
					navOpen = !navOpen;
				}}
			>
				<span class="sr-only">Open main menu</span>
				{#if navOpen}
					<X />
				{:else}
					<Menu />
				{/if}
			</button>
		</span>
	</div>
</nav>
