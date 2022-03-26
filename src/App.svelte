<script>
	import BarGraph from "./BarGraph.svelte";
	import Sheet from "./Sheet.svelte";

	let datas = [];
</script>

<main>
	<BarGraph datas={datas} />
	<Sheet datas={datas} />
	<form>
		<input type="text">
		<input type="number">
		<input type="submit" value="Enter">
	</form>
</main>

<style>

</style>