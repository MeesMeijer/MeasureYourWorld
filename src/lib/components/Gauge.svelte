<script lang="ts">
	// import { writable } from 'svelte/store';
	import { spring } from 'svelte/motion';
	// import { backInOut } from 'svelte/easing';
	import { arc as d3arc } from 'd3-shape';
	import { scaleLinear } from 'd3-scale';

    export let data: number[] | undefined;
    
	let width = 200;
	let height = 200;
    let value = spring(data?.at(-1) ? data?.at(-1) : 0, { stiffness: 0.1 });

    // console.log(data)
    // if (!data){
    //     let value = spring(0, { stiffness: 0.1 });

    // }else{
    //     let value = spring(data.at(-1), { stiffness: 0.1 });
    // }

	
	let min = 0;
	let max = 100;

	let startAngle = -123;
	let endAngle = 123;
	let innerRadius = 50;
	let outerRadius = 65;
	let cornerRadius = 10;
	let stopEl: SVGStopElement | undefined;

	$: {
		if ($value > 60) {
            stopEl?.setAttribute("stop-color", "red")
		}else{
            stopEl?.setAttribute("stop-color", "blue")
        }
	}

	$: scale = scaleLinear().domain([min, max]).range([startAngle, endAngle]);

	$: valueAngle = scale($value);

	$: arc = d3arc()
		.innerRadius(innerRadius)
		.outerRadius(outerRadius)
		.startAngle((startAngle * Math.PI) / 180)
		.endAngle((valueAngle * Math.PI) / 180)
		.cornerRadius(cornerRadius);

	$: trackArc = d3arc()
		.innerRadius(innerRadius)
		.outerRadius(outerRadius)
		.startAngle((startAngle * Math.PI) / 180)
		.endAngle((endAngle * Math.PI) / 180)
		.cornerRadius(cornerRadius);

</script>

<svg {width} {height} class="dark:bg-transparent mb-2">
	<path
		d={trackArc()}
		transform="translate({width / 2}, {height / 2})"
		class="track "
	/>
	<path d={arc()} transform="translate({width / 2}, {height / 2})"/>

	<text transform="translate({width / 2}, {height / 2})" dy={16}>
		{Math.round($value)}
	</text>



	<defs>
		<linearGradient id="fillGradient" x1="0" y1="0" x2="0" y2="100">
			<stop offset="100" bind:this={stopEl} stop-color="hsl(140, 100%, 50%)" />
		</linearGradient>
	</defs>
</svg>

<style>
	svg {
		/* background-color: hsl(0, 0%, 0%); */
		/* border: 0px solid #ddd; */
        border: none;
        /* margin-bottom: 3px; */
    }
	path {
		fill: url(#fillGradient);
		/* 		fill: red; */
		/* 		fill: conic-gradient(gold 40%, #f06 0); */
	}

	.track {
		stroke: hsla(0, 0%, 100%, 0.2);
		stroke-width: 2;
		fill: none;
	}

	text {
		fill: white;
		font-size: 2rem;
		text-anchor: middle;
	}

</style>
