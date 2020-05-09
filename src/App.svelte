<script>
	import Counter from "./components/Counter.svelte"
	import Image from "./components/Image.svelte"

	let sound;

	function play() {
		sound.play();
	}

</script>

<main class="w-full md:w-1/3 h-full bg-gray-100 flex flex-col items-center p-4">
	<h2 class="pb-6 font-bold text-2xl text-gray-700">Hand Washing App</h2>
	<Counter on:play={play} />
	<Image />
	<audio bind:this={sound}>
		<source src="sound.wav">
	</audio>
</main>