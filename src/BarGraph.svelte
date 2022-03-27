<script>
    export let datas;

    import Bar from "./Bar.svelte"

    $: largestValue = datas.length ? [...datas].sort((a,b) => a.value - b.value)[datas.length - 1].value : 0;  //Get the biggest value   
</script>

<main>
    {#each datas as data}
        <Bar data={data} largestValue={largestValue} />
    {/each}
</main>

<style>
    main {
        width: 100%;
        height: 60vh;
    }
</style>