<script>
	import '../app.postcss';
	import Navbar from '../components/Navbar.svelte';
</script>

<div class="w-full min-h-screen">
	<Navbar />
	<slot />
</div>