<script lang="ts">
	import { cn } from "$lib/utils.js";
	import { Tabs as TabsPrimitive } from "bits-ui";

	let {
		ref = $bindable(null),
		class: className,
		...restProps
	}: TabsPrimitive.ListProps = $props();
</script>

<TabsPrimitive.List
	bind:ref
	class={cn(
		"bg-muted text-muted-foreground inline-flex  items-center justify-center rounded-lg p-1",
		className,
	)}
	{...restProps}
/>
