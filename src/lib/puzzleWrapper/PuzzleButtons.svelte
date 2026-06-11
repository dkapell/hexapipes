<script>
	import Settings from '$lib/settings/Settings.svelte';
	import { createEventDispatcher } from 'svelte';

	export let solved = false;
	export let includeNewPuzzleButton = true;

	const dispatch = createEventDispatcher();

	function startOver() {
		if (window.confirm('Erase your progress and start over?')) {
			dispatch('startOver');
		}
	}

	function newPuzzle() {
		if (solved || window.confirm('Skip this puzzle and start a new one?')) {
			dispatch('newPuzzle');
		}
	}
	let showSettings = false;
</script>

<div class="row buttons">
	<div class='col text-center'>
	<!-- Start over button-->
	<button class='btn btn-outline-primary mx-1 btn-lg' on:click={startOver}> Start over </button>
	<!-- Settings button -->
	<button class='btn btn-outline-primary mx-1 btn-lg' on:click={() => (showSettings = !showSettings)}> Settings </button>
	<!-- New puzzle button -->
	{#if includeNewPuzzleButton}
		<button class='btn btn-outline-primary mx-1 btn-lg' on:click={newPuzzle}> New puzzle </button>
	{/if}
</div>
</div>

{#if showSettings}
	<Settings />
{/if}
