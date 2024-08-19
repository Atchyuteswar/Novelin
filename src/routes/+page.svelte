<script lang="ts">
	import { AspectRatio } from '$lib/components/ui/aspect-ratio/index.js';
	import book1 from '$lib/img/book-5.jpg?enhanced';
</script>

<main class="min-h-screen">
	<div class="container mx-auto p-6">
		<AspectRatio ratio={16 / 9} class="bg-muted">
			<enhanced:img
				src={book1}
				alt="Books by Jess Bailey"
				class="h-full w-full rounded-md object-cover"
			/>
		</AspectRatio>
	</div>

	<h1 class="text-center text-2xl text-yellow-400 dark:text-yellow-300 md:text-3xl lg:text-5xl">
		Dive into a World of Stories
	</h1>
</main>
