<script lang="ts">
	import { Chart, Card, A, Button, Dropdown, DropdownItem } from 'flowbite-svelte';
	import { ChevronRightSolid, ChevronDownSolid } from 'flowbite-svelte-icons';

    export let data: Array<[number,any]> | undefined;

    let dataList: any[] = [0]
    let categoriesList: any[] = [0]

    data?.forEach(e => {
        dataList.push(e[0])
        categoriesList.push(e[1])
    })

	let options: ApexCharts.ApexOptions = {
		chart: {
			height: '140px',
			type: 'area',
			fontFamily: 'Inter, sans-serif',
			dropShadow: {
				enabled: false
			},
			toolbar: {
				show: false
			}
		},
		tooltip: {
			enabled: false,
			x: {
				show: false
			}
		},
		fill: {
			type: 'gradient',
			gradient: {
				opacityFrom: 0.55,
				opacityTo: 0,
				shade: '#1C64F2',
				gradientToColors: ['#1C64F2']
			}
		},
		dataLabels: {
			enabled: false
		},
		stroke: {
			width: 6
		},
		grid: {
			show: true,
			strokeDashArray: 4,
			padding: {
				left: 0,
				right: 2,
				top: 0
			}
		},
		series: [
			{
				// name: 'C',
				data: dataList,
				color: '#1A56DB',
			}
		],
		xaxis: {
			categories: categoriesList,
			labels: {
				show: false
			},
			axisBorder: {
				show: false
			},
			axisTicks: {
				show: false
			}
		},
		yaxis: {
			show: true,
            forceNiceScale: true,
            labels:{
                offsetX: -10,
                style:{
                    colors: "gray"
                }
            }
		}
	};
</script>

<Card padding={"none"} class="p-3 pb-0 mb-2">
	<div class="flex justify-between">
		<div>
			<h5 class="leading-none text-2xl font-bold text-gray-900 dark:text-white pb-2">{dataList.at(-1)} C</h5>
			<!-- <p class="text-base font-normal text-gray-500 dark:text-gray-400"></p> -->
		</div>
	</div>
	<Chart {options} />
    
	<!-- <div class="grid grid-cols-1 items-center border-gray-200 border-t dark:border-gray-700 justify-between">
	</div> -->
</Card>
