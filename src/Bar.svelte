<script>
    export let data;
    export let largestValue;

    $: percentageValue = data.value / largestValue * 100;  // This length is base on the largest value of all

    setInterval(() => {
        console.log(percentageValue)
    });
    function randomColor() {
        return "#" + Math.floor(Math.random()*16777215).toString(16);
    }
</script>

<main>
    <span id="name">{data.name}</span>
    <div
        id="bar" 
        style="
            --percentage-width: {percentageValue}%;
            --color: {randomColor()};
        "
        value="{data.value}"
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
        --color: red;
        --percentage-width: 0%;
        display: inline-block;
        width: var(--percentage-width);
        height: inherit ;
        background-color: var(--color);
    }
    #bar::after {
        float: right;
        content: attr(value);
        /* overflow: hidden; */
    }
</style>