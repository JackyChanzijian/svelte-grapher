<script>
    export let datas;

    import Bar from "./Bar.svelte"
</script>

<main>
    {#each datas as data}
        <Bar data={data} />
    {/each}
</main>

<style>
    main {
        width: 100%;
        height: 60vh;
    }
</style>