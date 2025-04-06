<script>
    import ChevronDown from "@lucide/svelte/icons/chevron-down";

    import DollarSign from "@lucide/svelte/icons/dollar-sign";
    import FileCheck from "@lucide/svelte/icons/file-check-2";
    import FileWarning from "@lucide/svelte/icons/file-warning";
    import Plus from "@lucide/svelte/icons/plus";
    import Search from "@lucide/svelte/icons/search";

    import ContractsCard from "$lib/components/contracts-card.svelte";
    import Notifications from "$lib/components/notifications.svelte";
    import PageContainer from "$lib/components/page-container.svelte";
    import SummaryCard from "$lib/components/summary-card.svelte";
    import { Button, buttonVariants } from "$lib/components/ui/button";
    import * as DropdownMenu from "$lib/components/ui/dropdown-menu";
</script>

<PageContainer title="Peasy - Dashboard">
    {#snippet actions()}
        <div class="flex gap-2">
            <Button
                class="lg:w-48 size-9 shadow-none lg:justify-start lg:!text-muted-foreground lg:cursor-text !bg-transparent lg:pr-2"
                variant="outline"
            >
                <Search class="size-4" />
                <span class="mt-px hidden lg:flex"> Search... </span>

                <div class="flex-1 hidden justify-end lg:flex">
                    <kbd
                        class="flex rounded-sm w-fit bg-elevated border shadow-sm flex-center gap-1 font-mono font-semibold px-1"
                    >
                        ⌘+k
                    </kbd>
                </div>
            </Button>
            <div class="flex">
                <Button class="rounded-r-none border-r-blue-100 border-r-2">
                    <Plus class="size-4" />
                    New contract</Button
                >
                <DropdownMenu.Root>
                    <DropdownMenu.Trigger
                        class={buttonVariants({
                            class: "aspect-square p-0 rounded-l-none",
                        })}
                    >
                        <ChevronDown class="size-4" />
                    </DropdownMenu.Trigger>
                    <DropdownMenu.Content>
                        <DropdownMenu.Group>
                            <DropdownMenu.Item>Contract</DropdownMenu.Item>
                        </DropdownMenu.Group>
                    </DropdownMenu.Content>
                </DropdownMenu.Root>
            </div>
        </div>
    {/snippet}
    <div class="flex flex-1 flex-col p-3 h-full">
        <div class="flex lg:flex-row flex-col gap-3 h-full">
            <div class="lg:flex-[2] flex flex-col gap-3 h-min lg:h-full">
                <div class="grid grid-cols-2 gap-3 col-span-2 h-min">
                    <SummaryCard
                        icon={FileCheck}
                        title="Active Contracts"
                        total="150"
                        link="/contracts"
                    >
                        {#snippet hint()}
                            <span
                                class="text-xs bg-green-500/20 text-green-600 px-2 rounded-xl"
                                >+53%
                            </span>

                            from last month
                        {/snippet}
                    </SummaryCard>
                    <SummaryCard
                        icon={FileWarning}
                        title="Due Contracts"
                        total="15"
                    >
                        {#snippet hint()}
                            In the next 30 days
                        {/snippet}
                    </SummaryCard>
                    <SummaryCard icon={DollarSign} title="Spend" total="$1,432">
                        {#snippet hint()}
                            <span
                                class="text-xs bg-green-500/20 text-green-600 px-2 rounded-xl"
                                >+23%
                            </span>

                            from last month
                        {/snippet}
                    </SummaryCard>
                </div>
                <div class="h-0 flex-1 min-h-0 lg:block hidden">
                    <ContractsCard />
                </div>
            </div>
            <div class="lg:flex-1">
                <Notifications />
            </div>
            <div class="h-0 flex-1 min-h-0 lg:hidden">
                <ContractsCard />
            </div>
        </div>
    </div>
</PageContainer>
