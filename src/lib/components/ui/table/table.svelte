<script lang="ts">
	import { cn } from "$lib/utils.js";
	import type { WithElementRef } from "bits-ui";
	import type { HTMLTableAttributes } from "svelte/elements";

	let {
		ref = $bindable(null),
		class: className,
		children,
		...restProps
	}: WithElementRef<HTMLTableAttributes> = $props();
</script>

<div class="relative w-full overflow-auto px-3">
	<table
		bind:this={ref}
		class={cn("w-full caption-bottom  text-sm", className)}
		{...restProps}
	>
		{@render children?.()}
	</table>
</div>
