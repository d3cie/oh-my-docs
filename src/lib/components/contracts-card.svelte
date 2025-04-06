<script lang="ts">
    import ArrowLeft from "@lucide/svelte/icons/arrow-left";
    import ArrowRight from "@lucide/svelte/icons/arrow-right";

    import { ScrollArea } from "$lib/components/ui/scroll-area";
    import * as Table from "$lib/components/ui/table";

    import { Button } from "$lib/components/ui/button";
    import * as Select from "$lib/components/ui/select";

    const contracts: {
        id: string;
        name: string;
        totalAmount: string;
        description: string;
        dueDate: string;
    }[] = [
        {
            id: "CT001",
            name: "AWS Hosting",
            totalAmount: "$1200.00",
            description: "Annual AWS hosting services.",
            dueDate: "in 6 days",
        },
        {
            id: "CT002",
            name: "GitHub License",
            totalAmount: "$350.00",
            description: "Monthly GitHub Enterprise license.",
            dueDate: "in 12 days",
        },
        {
            id: "CT003",
            name: "Zoom Account",
            totalAmount: "$200.00",
            description: "Yearly Zoom business account.",
            dueDate: "in 18 days",
        },
        {
            id: "CT004",
            name: "Workspace",
            totalAmount: "$150.00",
            description: "Monthly Google Workspace subscription.",
            dueDate: "in 22 days",
        },
        {
            id: "CT005",
            name: "Slack Grid",
            totalAmount: "$400.00",
            description: "Annual Slack Enterprise Grid.",
            dueDate: "in 25 days",
        },
        {
            id: "CT006",
            name: "Cloudflare",
            totalAmount: "$90.00",
            description: "Monthly Cloudflare security services.",
            dueDate: "in 28 days",
        },
        {
            id: "CT007",
            name: "Azure Services",
            totalAmount: "$800.00",
            description: "Quarterly Microsoft Azure services.",
            dueDate: "in 30 days",
        },
        {
            id: "CT008",
            name: "Hetzner Services",
            totalAmount: "$322.00",
            description: "Monthly Microsoft Azure services.",
            dueDate: "in 30 days",
        },
        {
            id: "CT010",
            name: "Mintlify",
            totalAmount: "$29.00",
            description: "Monthly Mintlify subscroption for docs.",
            dueDate: "in 30 days",
        },
    ];
</script>

<div
    class="rounded-lg h-full overflow-hidden border text-card-foreground z-10 bg-background/40 shadow-sm transition-shadow backdrop-blur-none sm:backdrop-blur-sm flex flex-col min-h-0 relative"
>
    <div
        class="p-3 flex flex-row justify-between space-y-0 pb-0 md:pb-2 shadow-[inset_0_1px_0_0_white] rounded-t-lg"
    >
        <div
            class="tracking-tight text-xs font-medium md:text-sm flex flex-col"
        >
            <Select.Root value={"Due"} type="single" allowDeselect={false}>
                <Select.Trigger
                    class="z-10 h-6 w-fit justify-start gap-1 shadow-none border-none bg-secondary/60 p-0 px-2 text-sm font-semibold [&_svg]:size-3"
                >
                    Due Contracts
                </Select.Trigger>
                <Select.Content>
                    <Select.Group>
                        <Select.GroupHeading>filter</Select.GroupHeading>
                        {#each ["Active", "Due", "All"] as s}
                            <Select.Item value={s}>{s}</Select.Item>
                        {/each}
                    </Select.Group>
                </Select.Content>
            </Select.Root>
        </div>
        <div>
            <Button variant="secondary" size="sm" disabled class="size-6">
                <ArrowLeft />
            </Button>
            <Button variant="secondary" size="sm" class="size-6">
                <ArrowRight />
            </Button>
        </div>
    </div>

    <ScrollArea class="size-full min-h-0">
        <Table.Root class="h-full">
            <Table.Header>
                <Table.Row>
                    <Table.Head class="w-[100px]"></Table.Head>
                    <Table.Head>Name</Table.Head>
                    <Table.Head>Description</Table.Head>
                    <Table.Head>Due</Table.Head>
                    <Table.Head class="text-right">Amount</Table.Head>
                </Table.Row>
            </Table.Header>
            <Table.Body>
                {#each contracts as c (c)}
                    <Table.Row class="text-sm">
                        <Table.Cell class="font-medium">
                            <a
                                href="/contracts/{c.id}"
                                class="text-primary underline underline-offset-[3px]"
                            >
                                {c.id}
                            </a>
                        </Table.Cell>
                        <Table.Cell>{c.name}</Table.Cell>
                        <Table.Cell>{c.description}</Table.Cell>
                        <Table.Cell class="text-left">{c.dueDate}</Table.Cell>
                        <Table.Cell class="text-right"
                            >{c.totalAmount}</Table.Cell
                        >
                    </Table.Row>
                {/each}
            </Table.Body>
        </Table.Root>
    </ScrollArea>
    <div
        class="p-2 h-8 text-muted-foreground text-sm justify-between flex w-full items-end bg-gradient-to-t from-white to-transparent absolute bottom-0"
    ></div>
</div>
