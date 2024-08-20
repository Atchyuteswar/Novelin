<script lang="ts">
	import { AspectRatio } from '$lib/components/ui/aspect-ratio/index.js';
	import book1 from '$lib/img/book-5.jpg?enhanced';
	import book2 from '$lib/img/pexels-itismowgli-824197.jpg?enhanced';
	import book3 from '$lib/img/pexels-mccutcheon-1148399.jpg?enhanced';
	import book4 from '$lib/img/pexels-perfecto-capucine-515848-1329571.jpg?enhanced';
	const featuredBooks = [
		{
			src: book2,
			name: 'Photo by Parth Shah'
		},
		{
			src: book3,
			name: 'Photo by Brett McCutcheon'
		},
		{
			src: book4,
			name: 'Photo by Perfecto Capucine'
		}
	];
</script>

<main class="min-h-screen">
	<div class="container mx-auto p-6">
		<AspectRatio ratio={16 / 9} class="bg-muted">
			<enhanced:img
				src={book1}
				alt="Photo by Jess Bailey"
				class="h-full w-full rounded-md object-cover"
			/>
		</AspectRatio>
	</div>

	<h1 class="text-center text-2xl text-yellow-400 dark:text-yellow-300 md:text-3xl lg:text-5xl">
		Dive into a World of Stories
	</h1>
	<div class="mx-auto flex flex-col space-y-6 p-6 lg:flex-row lg:space-x-6 lg:space-y-0">
		{#each featuredBooks as book}
			<div class="aspect-square bg-muted lg:aspect-[1/2]">
				<enhanced:img
					src={book.src}
					alt="Photo by Jess Bailey"
					class="size-full rounded-md object-cover"
				/>
			</div>
		{/each}
	</div>
</main>
