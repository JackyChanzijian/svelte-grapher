<script>
    export let data;

    function randomColor() {
        return "#" + Math.floor(Math.random()*16777215).toString(16);
    }
</script>

<main>
    <span>{data.name}</span>
    <div
        class="bar" 
        style="
            --width: {data.value}px;
            --color: {randomColor()};
        "
    >
    </div>
</main>

<style>
    main {
        display: flex;
    }
    .bar {
        --width: 0px;
        --color: red;
        display: inline-block;
        width: var(--width);
        height: inherit ;
        background-color: var(--color);
    }
</style>