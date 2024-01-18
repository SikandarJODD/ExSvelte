<script>
	import Navbar from '$lib/home/Navbar.svelte';
	import '../app.pcss';
	import { ModeWatcher } from 'mode-watcher';
</script>

<ModeWatcher />
<Navbar />
<slot />
