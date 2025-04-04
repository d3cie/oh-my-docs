<script>
    import SummaryCard from "$lib/components/summary-card.svelte";
    import FileCheck from "@lucide/svelte/icons/file-check-2";
</script>

<div class="flex flex-1 flex-col gap-4 p-4 pt-0">
    <h1 class="text-4xl text-secondary-foreground font-bold">
        Good day, Decie
    </h1>
    <h3>here's an overview of your contracts and subscriptions</h3>
    <div class="gap-w-full">
        <div class="grid grid-cols-1 gap-4 md:grid-cols-2 lg:grid-cols-3">
            <SummaryCard
                icon={FileCheck}
                title="Active Contracts"
                trendPc={53}
                total="15"
                trend="up"
            />
        </div>
    </div>
</div>
