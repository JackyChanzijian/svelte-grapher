<script>
import { onMount } from "svelte";

	import BarGraph from "./BarGraph.svelte";
	import Sheet from "./Sheet.svelte";

	let datas = [];
	
	let dataValue = 0;
	let dataName = "";

	let isAutoSave = true;

	$: console.log(isAutoSave);
	// Autosave if the check box is checked and datas changed
	$: if (isAutoSave) {
		datas;
		saveDatas();
	}	
	// This will invoke on web start
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
		if (localStorage.getItem("datas") !== undefined) {
			datas = JSON.parse(localStorage.getItem("datas"));
			console.log("Datas get");
		}
		else {
			datas = [];
			console.log("Can't get datas");
		}
	}
</script>

<main>
	<BarGraph datas={datas} />
	<Sheet datas={datas} />
	<form>
		<input type="text" placeholder="Name" bind:value={dataName}>
		<input type="number" placeholder="Value" bind:value={dataValue}>
		<input type="button" value="Enter" on:click={addData}>
		<input type="button" value="Clear Data" on:click={clearDatas}>
		<input type="button" value="Save Data" on:click={saveDatas}>
		<input type="checkbox" name="Auto Save" bind:checked={isAutoSave}>
	</form>
</main>

<style>

</style>