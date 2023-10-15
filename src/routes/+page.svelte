<script lang="ts">
	import Counter from './Counter.svelte';
	import type { CounterProps } from '../types';

	let counters: Array<CounterProps> = [
		{
			title: 'new',
			value: 0
		}
	];

	$: titleList = counters.map((counter) => counter.title).join(', ');
	$: sum = counters
		.map((counter) => counter.value)
		.reduce((total, currentValue) => (total += currentValue), 0);

	function handleAdd() {
		counters = [
			...counters,
			{
				title: 'new',
				value: 0
			}
		];
	}

	function handleDelete(index: number) {
		counters.splice(index, 1);
		counters = counters;
	}
</script>

<svelte:head>
	<title>Multiple Counter</title>
	<meta name="description" content="Mutiple Counter" />
</svelte:head>

<div class="text-center">
	<h1 class="text-6xl">Multiple Counter</h1>

	{#each counters as counter, i}
		<Counter
			bind:title={counter.title}
			bind:value={counter.value}
			index={i}
			onDelete={handleDelete}
		/>
	{/each}

	<button
		class="max-w-sm m-auto text-center bg-green-400 rounded text-white cursor-pointer w-full"
		on:click={handleAdd}
	>
		new counter
	</button>

	<p>title list: {titleList}</p>
	<p>sum of count: {sum}</p>
</div>

<style>
</style>
