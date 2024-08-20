<script lang="ts">
	import { AspectRatio } from '$lib/components/ui/aspect-ratio/index.js';
	import book1 from '$lib/img/book-5.jpg?enhanced';
	import book2 from '$lib/img/pexels-itismowgli-824197.jpg?enhanced';
	import book3 from '$lib/img/pexels-mccutcheon-1148399.jpg?enhanced';
	import book4 from '$lib/img/pexels-perfecto-capucine-515848-1329571.jpg?enhanced';
	import { AudioLines, BookHeart, Heart } from 'lucide-svelte';
	const featuredBooks = [
		{
			src: book2,
			name: 'Photo by Parth Shah',
			text: {
				head: 'Upload Your Books',
				body: 'Share your stories with the world and reach a wide audience.'
			}
		},
		{
			src: book3,
			name: 'Photo by Brett McCutcheon',
			text: {
				head: 'Read for Free',
				body: 'Access a vast library of books without any cost.'
			}
		},
		{
			src: book4,
			name: 'Photo by Perfecto Capucine',
			text: {
				head: 'Connect',
				body: 'Join our community, share your thoughts, and discover new favorites.'
			}
		}
	];
</script>

<main class="min-h-screen">
	<div class="container relative mx-auto p-6">
		<AspectRatio ratio={16 / 9} class="bg-muted">
			<enhanced:img
				src={book1}
				alt="Photo by Jess Bailey"
				class="h-full w-full rounded-md object-cover brightness-[.5]"
			/>
		</AspectRatio>
		<h1
			class="absolute bottom-10 right-7 text-center text-2xl font-bold text-yellow-400 dark:text-yellow-300 md:text-3xl lg:text-5xl"
		>
			Dive into a World of Stories
		</h1>
	</div>

	<div class="mx-auto flex flex-col space-y-6 p-6 lg:flex-row lg:space-x-6 lg:space-y-0">
		{#each featuredBooks as book}
			<div class="relative aspect-square bg-muted lg:aspect-[1/2]">
				<enhanced:img
					src={book.src}
					alt={book.name}
					class="size-full rounded-md object-cover brightness-[.6]"
				/>
				<h3
					class="absolute bottom-0 right-7 p-3 font-mono text-xl text-yellow-400 shadow-red-700 [text-shadow:_2px_1px_1px_var(--tw-shadow-color)] dark:text-yellow-300 md:text-2xl lg:text-3xl"
				>
					{book.text.body}
				</h3>
			</div>
		{/each}
	</div>
</main>
<section class="p-10">
	<h3 class="text-2xl md:text-4xl">
		<span class="flex items-center">
			We're bookworms, <BookHeart size={30} />
		</span>
		<span class="flex items-center"> storytellers, <AudioLines size={30} /> </span>
		<span class="flex items-center"> and dreamers at heart. <Heart size={30} /> </span>
		Our digital library is home to thousands of titles, from classic novels to the latest bestsellers.
		Find your next favorite read on NovelIn!
	</h3>
</section>
