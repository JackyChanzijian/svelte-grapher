<script>
import { onMount } from "svelte";

	import BarGraph from "./BarGraph.svelte";
	import Sheet from "./Sheet.svelte";

	let datas = [{ name: "test1", value: 1000}, { name: "test2", value: 980}];
	
	let dataValue = 0;
	let dataName = "";

	$: console.table(datas);

	onMount(() => {
		getDatas();
	})
	// Handle input
	function addData() {
		datas = [{name: dataName, value: dataValue}, ...datas];	// Add input field to datas array
		//Clear input field
		dataValue = 0;
		dataName = "";	
	}
	function clearDatas() {
		datas = [];
	}
	function saveDatas() {
		localStorage.setItem("datas", JSON.stringify(datas));
	}
	function getDatas() {
		if (localStorage.getItem("datas") !== null) {
			datas = JSON.parse(localStorage.getItem("datas"));
			console.log(123)
		}
		else {
			datas = [];
		}
	}
</script>

<main>
	<BarGraph datas={datas} />
	<Sheet datas={datas} />
	<form>
		<input type="text" bind:value={dataName}>
		<input type="number" bind:value={dataValue}>
		<input type="button" value="Enter" on:click={addData}>
		<input type="button" value="Clear Data" on:click={clearDatas}>
		<input type="button" value="Save Data" on:click={saveDatas}>
	</form>
</main>

<style>

</style>