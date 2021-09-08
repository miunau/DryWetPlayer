<script>
	import DryWetPlayer from "./DryWetPlayer.svelte";
	export let name;
</script>

<main>
	<DryWetPlayer dryMp3Url="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" wetMp3Url="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3" />
	<DryWetPlayer dryMp3Url="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-3.mp3" wetMp3Url="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-4.mp3" />
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>