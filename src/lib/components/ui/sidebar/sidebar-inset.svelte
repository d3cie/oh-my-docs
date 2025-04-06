<script lang="ts">
	import { cn } from "$lib/utils.js";
	import type { WithElementRef } from "bits-ui";
	import type { HTMLAttributes } from "svelte/elements";

	let {
		ref = $bindable(null),
		class: className,
		children,
		...restProps
	}: WithElementRef<HTMLAttributes<HTMLElement>> = $props();
</script>

<main
	bind:this={ref}
	class={cn(
		"bg-background relative flex flex-1 flex-col",
		"sm:h-[calc(100dvh-theme(spacing.4))] md:mt-4 md:peer-data-[state=collapsed]:ml-2 md:ml-0 md:rounded-tl-xl md:shadow",
		className,
	)}
	{...restProps}
>
	{@render children?.()}
</main>
