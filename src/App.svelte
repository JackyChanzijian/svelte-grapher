<script>
	import BarGraph from "./BarGraph.svelte";
	import Sheet from "./Sheet.svelte";

	let datas = [];
	
	let dataValue = 0;
	let dataName = "";

	$: console.table(datas);

	// Handle input
	function addData() {
		datas = [{name: dataName, value: dataValue}, ...datas];	// Add input field to datas array
		//Clear input field
		dataValue = 0;
		dataName = "";	
	}

</script>

<main>
	<BarGraph datas={datas} />
	<Sheet datas={datas} />
	<form>
		<input type="text" bind:value={dataName}>
		<input type="number" bind:value={dataValue}>
		<input type="button" value="Enter" on:click={addData}>
	</form>
</main>

<style>

</style>