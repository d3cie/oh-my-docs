<script>
    import AlertCircle from "@lucide/svelte/icons/alert-circle";
    import ArrowRight from "@lucide/svelte/icons/arrow-right";
    import CheckCircle from "@lucide/svelte/icons/check-circle";
    import FileText from "@lucide/svelte/icons/file-text";
    import RefreshCw from "@lucide/svelte/icons/refresh-cw";
    import ScrollArea from "./ui/scroll-area/scroll-area.svelte";

    import { Button } from "$lib/components/ui/button";

    const notifications = [
        {
            id: 1,
            title: "Contract Expiring Soon",
            description: "Service Agreement with Acme Inc expires in 15 days",
            time: "2 hours ago",
            icon: AlertCircle,
            iconClass: "text-orange-500",
        },
        {
            id: 2,
            title: "Document Uploaded",
            description: "New NDA document has been uploaded",
            time: "Yesterday",
            icon: FileText,
            iconClass: "text-blue-500",
        },
        {
            id: 3,
            title: "Renewal Completed",
            description: "Software Subscription has been renewed",
            time: "2 days ago",
            icon: CheckCircle,
            iconClass: "text-green-500",
        },
        {
            id: 4,
            title: "Renewal Reminder",
            description: "Office Lease needs renewal decision",
            time: "3 days ago",
            icon: RefreshCw,
            iconClass: "text-purple-500",
        },
        {
            id: 5,
            title: "New Contract Created",
            description: "New contract created with Acme Inc",
            time: "4 days ago",
            icon: FileText,
            iconClass: "text-blue-500",
        },
        {
            id: 6,
            title: "New Subscription Added",
            description: "Subscription with Resend has been added",
            time: "5 days ago",
            icon: FileText,
            iconClass: "text-blue-500",
        },
        {
            id: 7,
            title: "New Subscription Added",
            description: "Subscription with Resend has been added",
            time: "7 days ago",
            icon: FileText,
            iconClass: "text-blue-500",
        },
    ];
</script>

<div
    class="rounded-lg border text-card-foreground relative z-10 bg-background/40 hover:shadow-md transition-shadow backdrop-blur-none sm:backdrop-blur-sm flex flex-col min-h-0 h-full"
>
    <div
        class="p-3 sm:p-4 flex flex-row justify-between space-y-0 pb-0 md:pb-2 shadow-[inset_0_1px_0_0_white] rounded-t-lg"
    >
        <div
            class="tracking-tight text-xs font-medium md:text-sm flex flex-col"
        >
            Notifications
            <p class="text-muted-foreground">Recent alerts and activity</p>
        </div>
    </div>

    <ScrollArea
        class="[mask-image:linear-gradient(to_bottom,_black_75%,_transparent)]"
    >
        <div class="flex h-full p-3 sm:p-4 flex-col min-h-0">
            {#each notifications as notification}
                <div class="flex gap-3">
                    <div class="grid">
                        <div class="flex items-center gap-3">
                            <div
                                class="border rounded-full size-6 flex items-center justify-center bg-white"
                            >
                                <!-- svelte-ignore svelte_component_deprecated: @lucide/svelte version not compatible with svelte 5 syntax -->
                                <svelte:component
                                    this={notification.icon}
                                    class="size-4 inline text-muted-foreground {notification.iconClass}"
                                ></svelte:component>
                            </div>
                            <p
                                class="text-sm font-medium flex items-center gap-2"
                            >
                                {notification.title}
                            </p>
                        </div>
                        <div
                            class="border-l pl-6 ml-3 pb-4 [mask-image:linear-gradient(to_bottom,_black_70%,_transparent)]"
                        >
                            <p class="text-xs text-muted-foreground">
                                {notification.description}
                            </p>
                            <p class="text-xs text-muted-foreground">
                                {notification.time}
                            </p>
                        </div>
                    </div>
                </div>
            {/each}
        </div>
        <!-- <div
            class="bg-gradient-to-t from-background/40 to-transparent absolute w-full h-24 bottom-0"
        ></div> -->
    </ScrollArea>

    <div class="w-full p-3 items-end flex flex-1">
        <Button class="w-full" variant="outline" href="/notifications"
            >View all notifications <ArrowRight />
        </Button>
    </div>
</div>
