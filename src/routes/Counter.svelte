<script lang="ts">
	function handlePlus() {
		value += 1;
	}

	function handleMinus() {
		if (value == 0) return;

		value -= 1;
	}

	function handleReset() {
		value = 0;
	}

	export let index = 0;
	export let value = 0;
	export let title = '';
	export let onDelete = () => {};
</script>

<div class="counter">
	<div
		class="max-w-sm rounded border-solide bg-gray-100 shadow-lg m-auto flex relative items-center mb-2"
	>
		<input class="text-gray-600 mx-4 px-1 w-32" bind:value={title} />
		<span class="text-lg font-bold px-4 absolute centerize"> {value} </span>
		<div class="ml-auto">
			<button class="btn bg-red-500 rounded-l" on:click={handlePlus}>+</button>
			<button class="btn bg-blue-500" on:click={handleMinus}>-</button>
			<button class="btn bg-yellow-500 rounded-r" on:click={handleReset}>0</button>
			<button class="text-gray-500 cursor-pointer px-4" on:click={() => onDelete(index)}>
				x
			</button>
		</div>
	</div>
</div>

<style>
	.centerize {
		left: 50%;
		transform: translateX(-50%);
	}

	.btn {
		--text-opacity: 1;
		color: #fff;
		color: rgba(255, 255, 255, var(--text-opacity));
		padding-top: 0.25rem;
		padding-bottom: 0.25rem;
		padding-left: 0.75rem;
		padding-right: 0.75rem;
		margin-top: 0.25rem;
		margin-bottom: 0.25rem;
		font-size: 1.125rem;
	}
</style>
