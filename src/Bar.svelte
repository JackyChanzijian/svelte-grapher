<script>
    export let data;

    function randomColor() {
        return "#" + Math.floor(Math.random()*16777215).toString(16);
    }
</script>

<main>
    <span id="name">{data.name}</span>
    <div
        id="bar" 
        style="
            --width: {data.value}px;
            --color: {randomColor()};
        "
        content="{data.value}"
    >
    </div>
</main>

<style>
    main {
        display: flex;
    }
    #name {
        width: 60px;
    }
    #bar {
        --width: 0px;
        --color: red;
        display: inline-block;
        width: var(--width);
        height: inherit ;
        background-color: var(--color);
    }
    #bar::after {
        float: right;
        content: attr(content);
        /* overflow: hidden; */
    }
</style>