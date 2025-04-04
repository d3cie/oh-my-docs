<script lang="ts">
    import TrendingDown from "@lucide/svelte/icons/trending-down";
    import TrendingUp from "@lucide/svelte/icons/trending-up";

    let {
        total,
        title,
        icon,
        trend,
        trendPc,
    }: {
        total: string;
        title: string;
        icon: any;
        trend: "up" | "down";
        trendPc: number;
    } = $props();
</script>

<div
    class="rounded-lg border text-card-foreground relative z-10 bg-background/60 shadow-none sm:shadow-md backdrop-blur-none sm:backdrop-blur-sm"
>
    <div
        class="p-3 sm:p-4 md:p-6 flex flex-row items-center justify-between space-y-0 pb-0 md:pb-2"
    >
        <div class="tracking-tight text-xs font-medium md:text-sm">
            {title}
        </div>

        <!-- svelte-ignore svelte_component_deprecated: @lucide/svelte version not compatible with svelte 5 syntax -->
        <svelte:component
            this={icon}
            class="size-3 md:size-4 text-muted-foreground"
        ></svelte:component>
    </div>
    <div class="p-3 sm:p-4 md:p-6 pt-0 md:pt-0 sm:pt-0">
        <h2 class="text-base font-bold md:text-2xl">{total}</h2>
        <span
            class="flex items-center gap-2 text-xs text-muted-foreground md:text-sm"
        >
            <p class="text-xs text-muted-foreground md:text-sm">
                {trendPc}% up from last month
            </p>
            {#if trend == "up"}
                <TrendingUp class="size-3 text-muted-foreground md:size-4" />
            {:else}
                <TrendingDown class="size-3 text-muted-foreground md:size-4" />
            {/if}
        </span>
    </div>
</div>
