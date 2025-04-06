<script lang="ts">
    import * as Sidebar from "$lib/components/ui/sidebar";
    import type { Snippet } from "svelte";
    import Separator from "./ui/separator/separator.svelte";

    let {
        children,
        title,
        actions,
    }: {
        children: Snippet;
        actions?: Snippet;
        title: string;
    } = $props();
</script>

<Sidebar.Inset class="border !shadow flex flex-col relative bg-white/60">
    <header
        class="flex h-14 shrink-0 items-center gap-2 border-b w-full shadow-[inset_0_1px_0_0_white] rounded-t-xl"
    >
        <div class="flex items-center gap-2 px-5">
            <Sidebar.Trigger class="-ml-1" />
            <Separator orientation="vertical" class="mr-1 ml-1 h-6" />
            <span class="text-secondary-foreground font-semibold mt-0.5">
                {title}
            </span>
        </div>
        <div class="flex-1 flex items-center justify-end w-full">
            {@render actions?.()}
        </div>
    </header>
    <div class="overflow-y-scroll overflow-x-hidden h-full">
        {@render children()}
    </div>
</Sidebar.Inset>
