<script lang="ts">
	import { AspectRatio } from '$lib/components/ui/aspect-ratio/index.js';
	import book1 from '$lib/img/book-5.jpg';
</script>

<div class="container mx-auto p-6">
	<AspectRatio ratio={16 / 9} class="bg-muted">
		<enhanced:img
			src={book1}
			alt="Gray by Drew Beamer"
			class="h-full w-full rounded-md object-cover"
		/>
	</AspectRatio>
</div>

<h1>Dive into a World of Stories</h1>
