<script>
	import Footer from '$lib/layout/Footer.svelte';
	import Header from '$lib/layout/Header.svelte';
	
</script>


<div class="min-h-screen bg-background font-sans antialiased">
	<Header />
	<div class="mx-auto flex-1 overflow-hidden">
		<slot></slot>
	</div>
	<Footer />
</div>
