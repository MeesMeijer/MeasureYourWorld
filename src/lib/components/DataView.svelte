<script lang="ts">
    import Gauge from "./Gauge.svelte";
    import {
		Button,
        Card,
        Indicator,
        Tooltip
    } from "flowbite-svelte"

    import Chart from "./Chart.svelte";

    export let type = "gauge" || "chart";
    export let options: DataViewOptions;
    
    type DataViewOptions  = {
        sensor: {
            name: string,
            uuid: string
            connection:{
                ip?: string,
                online: boolean,
                lastOnline?: Date
            }
        },
        chartData?: Array<[any,any]>
        gaugeData?: Array<any>,
        type: "gauge" | "chart"
    }

</script>

<Card padding={"md"} class="relative m-2 ">
    <h5 class="flex flex-col relative text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{options.sensor.name}
        <Indicator color="{options.sensor.connection.online ? "green" : "red"}" border size="xl" placement="center-right">
            <span class="text-white text-xs font-bold">?</span>
        </Indicator>
        <Tooltip>
           {options.sensor.connection.online ? "Online" : "Offline"}
        </Tooltip>
    </h5>

    <span class="mt-1 mb-2 p-0 text-sm" >
        uuid: {options.sensor.uuid}
    </span>
    
    {#if type == "gauge"}
        <Gauge data={options.gaugeData}></Gauge>
    {:else if type == "chart"}
        <Chart data={options.chartData}></Chart>
    {/if}
    
    <Button href="../sensor/{options.sensor.uuid}" color="blue" class="mb-0 bottom-0" >
        Details
    </Button>
</Card>