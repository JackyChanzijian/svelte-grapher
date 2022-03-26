<script>
    export let data;
</script>

<main>
    <span>{data.name}</span>
    <div class="bar" style="--width: {data.value}px"></div>
</main>

<style>
    main {
        display: flex;
    }
    .bar {
        --width: 0px;
        display: inline-block;
        width: var(--width);
        height: inherit ;
        background-color: red;
    }
</style>