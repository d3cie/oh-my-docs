<script lang="ts">
	import AppSidebar from "$lib/components/app-sidebar.svelte";
	import * as Sidebar from "$lib/components/ui/sidebar";

	import "../app.css";

	import "@fontsource-variable/nunito-sans";

	let { children } = $props();
</script>

<Sidebar.Provider>
	<div class="absolute inset-0 overflow-hidden w-full h-full">
		<div
			class="absolute top-10 left-10 w-72 h-72 bg-blue-400 rounded-full blur-[220px] opacity-5"
		></div>
		<div
			class="absolute bottom-20 right-20 w-96 h-96 bg-blue-400 rounded-full blur-[220px] opacity-10"
		></div>
		<div
			class="absolute top-1/2 left-1/2 w-80 h-80 bg-blue-400 rounded-full blur-[220px] opacity-5 translate-x-[-50%] translate-y-[-50%]"
		></div>
	</div>
	<AppSidebar />
	{@render children()}
</Sidebar.Provider>
