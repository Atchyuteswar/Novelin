<script lang="ts">
	import Navbar from '$lib/components/blocks/Navbar.svelte';
	import '../app.css';
	import { ModeWatcher } from 'mode-watcher';
</script>

<ModeWatcher />
<Navbar />
<slot />
