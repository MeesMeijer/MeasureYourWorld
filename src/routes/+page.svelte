<script lang="ts">

    import DataView from "$lib/components/DataView.svelte";
	// import { onMount } from "svelte";

    $:  sensors = [
            {
                sensor: { 
                    name: 'Sensor 1',
                    uuid: "111-111-111-111",
                    connection:{
                        online: false
                    }
                },
                type: "gauge"
            },
            {
                sensor: { 
                    name: 'Sensor 2',
                    uuid: "222-222-222-222",
                    connection:{
                        online: true
                    }
                },
                type: "chart"
            }
        ]

</script>

<div class="flex flex-wrap">

    {#each sensors as sensor}
        <DataView type={sensor.type} options={sensor}></DataView>
    {/each}

</div>