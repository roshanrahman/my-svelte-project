<script lang="ts">
	export let name: string;
	export let count: number = 0;
	let isShiftHeld = false;

	let incrementCount = () => {
		if (isShiftHeld) {
			count += 10;
		} else {
			count += 1;
		}
	};

	let handleKeydown = (event: KeyboardEvent) => {
		if (event.key === "Shift") {
			isShiftHeld = true;
		}
	};

	let handleKeyUp = (event: KeyboardEvent) => {
		if (event.key === "Shift") {
			isShiftHeld = false;
		}
	};
</script>

<svelte:window on:keydown={handleKeydown} on:keyup={handleKeyUp} />

<main>
	<h1>{count === 69 ? "Nice" : `Hello ${name}!`}</h1>
	<p>
		Hold <kbd>Shift</kbd> to increment by 10.
	</p>
	<button on:click={incrementCount} type="primary">
		{count > 0
			? `You clicked me ${count} time${count > 1 ? "s" : ""}.`
			: "Click me to see what happens!"}
	</button>
	<button
		on:click={() => {
			count = 0;
		}}>Reset</button
	>
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

	button {
		outline: none;
		border: none;
		padding: 0.6em 1em;
		margin: 0.3em;
		border-radius: 0.3em;
		box-shadow: 1px 3px 7px 0px rgba(0, 0, 0, 0.116);
	}

	button[type="primary"] {
		color: white;
		background-color: #ff3e00;
	}
	button[type="primary"]:hover {
		background-color: #ff5e00;
	}
	button[type="primary"]:active {
		background-color: #ff3e00;
	}
</style>
