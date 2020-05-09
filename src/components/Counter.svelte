<script>
	import ProgressBar from "./ProgressBar.svelte";
	import {createEventDispatcher} from "svelte";

	let counter = 0;
	let myInterval = null;
	const dispatch = createEventDispatcher();

	$: if(counter === 20) {
		clearInterval(myInterval);
		counter = 0;
	} 

	$: counter === 10 && dispatch('play');

	$: percentage = Math.ceil((counter / 20) * 100);

	const start = () => {
		myInterval = setInterval(() => {
			counter++;
		}, 1000);
	}
</script>

<main class="w-full flex flex-col justify-between h-32 items-center">
	<ProgressBar {percentage} />
	{#if counter === 0}
	<button on:click={start} class="flex items-center justify-center rounded-full w-20 h-20">
		<svg xmlns="http://www.w3.org/2000/svg" class="w-12 h-12" viewBox="0 0 41.999 41.999">
			<path d="M36.068 20.176l-29-20A1 1 0 1 0 5.5.999v40a1 1 0 0 0 1.568.823l29-20a.999.999 0 0 0 0-1.646z"/>
		</svg>
	</button>
	{:else}
		<h2 class="font-bold text-md text-gray-500">{21 - counter} seconds left</h2>
	{/if}
</main>