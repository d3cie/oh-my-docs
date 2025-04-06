<script lang="ts" module>
	import CircleGauge from "@lucide/svelte/icons/circle-gauge";
	import FileText from "@lucide/svelte/icons/file-text";
	import Settings2 from "@lucide/svelte/icons/settings-2";

	const data = {
		user: {
			name: "decie",
			email: "decie@peasy.so",
			avatar: "https://peasy.so/decie.jpg",
		},
		navMain: [
			{
				title: "Dashboard",
				url: "/",
				icon: CircleGauge,
				isActive: true,
			},
			{
				title: "Contracts",
				url: "/contracts",
				icon: FileText,
				isActive: false,
				items: [
					{
						title: "Postmark",
						url: "#",
					},
					{
						title: "Aws",
						url: "#",
					},
				],
			},
			{
				title: "Settings",
				url: "#",
				icon: Settings2,
				items: [
					{
						title: "General",
						url: "#",
					},
					{
						title: "Team",
						url: "#",
					},
					{
						title: "Billing",
						url: "#",
					},
				],
			},
		],
	};
</script>

<script lang="ts">
	import NavMain from "$lib/components/nav-main.svelte";
	import NavUser from "$lib/components/nav-user.svelte";
	import * as Sidebar from "$lib/components/ui/sidebar/index.js";
	import Command from "@lucide/svelte/icons/command";
	import type { ComponentProps } from "svelte";

	let {
		ref = $bindable(null),
		...restProps
	}: ComponentProps<typeof Sidebar.Root> = $props();
</script>

<Sidebar.Root bind:ref variant="inset" {...restProps}>
	<Sidebar.Header>
		<Sidebar.Menu>
			<Sidebar.MenuItem>
				<Sidebar.MenuButton size="lg">
					{#snippet child({ props })}
						<a href="##" {...props}>
							<div
								class="bg-sidebar-primary text-sidebar-primary-foreground flex aspect-square size-8 items-center justify-center rounded-lg"
							>
								<Command class="size-4" />
							</div>
							<div
								class="grid flex-1 text-left text-sm leading-tight"
							>
								<span class="truncate font-semibold"
									>Oh my docs</span
								>
							</div>
						</a>
					{/snippet}
				</Sidebar.MenuButton>
			</Sidebar.MenuItem>
		</Sidebar.Menu>
	</Sidebar.Header>
	<Sidebar.Content>
		<NavMain items={data.navMain} />
	</Sidebar.Content>
	<Sidebar.Footer>
		<NavUser user={data.user} />
	</Sidebar.Footer>
</Sidebar.Root>
