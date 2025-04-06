<script lang="ts">
    import { Separator } from "$lib/components/ui/separator";
    import * as Sidebar from "$lib/components/ui/sidebar";
    import type { Snippet } from "svelte";

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
        class="flex p-1.5 shrink-0 items-center gap-2 border-b w-full shadow-[inset_0_1px_0_0_white] rounded-t-xl"
    >
        <div class="flex items-center gap-2 px-2">
            <Sidebar.Trigger />
            <Separator orientation="vertical" class="mr-1 ml-0.5 h-7" />
            <span class="text-secondary-foreground font-semibold">
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
