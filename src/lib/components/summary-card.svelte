<script lang="ts">
    import type { Snippet } from "svelte";

    let {
        title,
        icon,
        total,
        hint,
        link,
    }: {
        title: string;
        icon: any;
        total: string;
        hint: Snippet;
        link?: string;
    } = $props();
</script>

<div
    class="hover:bg-blue-500/5 group transition-colors shadow-sm rounded-lg pt-4 bg-gray-100 border relative"
>
    <div
        class={"rounded-lg -m-px border group-hover:border-primary transition-colors text-card-foreground relative z-10 bg-gradient-to-bl from-blue-500/5 via-background/40  to-white  cursor-pointer shadow-[inset_0_1px_0_0_white] backdrop-blur-none h-min"}
    >
        <div class="p-3 flex flex-row items-center justify-between">
            <div
                class="tracking-tight text-xs font-medium md:text-sm flex items-center gap-1"
            >
                {title}
            </div>

            <div
                class="size-7 border rounded-full flex items-center justify-center absolute -top-3 right-3 bg-gray-50 shadow-[inset_0_1px_0_0_white]"
            >
                <!-- svelte-ignore svelte_component_deprecated -->
                <svelte:component
                    this={icon}
                    class="size-3.5 text-secondary-foreground stroke-[1.8px]"
                ></svelte:component>
            </div>
        </div>
        <div class="px-3 pb-2">
            <h2 class="text-base font-bold md:text-xl">{total}</h2>
            <span
                class="flex items-center gap-2 text-xs text-muted-foreground md:text-sm"
            >
                <p
                    class="text-xs text-muted-foreground md:text-sm flex items-center gap-1"
                >
                    {@render hint()}
                </p>
            </span>
        </div>
    </div>
</div>
