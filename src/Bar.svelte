<script>
    export let data;
    export let largestValue;

    $: percentageValue = data.value / largestValue * 100;  // This length is base on the largest value of all
    
    //  The percentage that animate(follow) the actual percentage when it changed
    let animatePercentage = 0;
    setInterval(() => {
        if (Math.abs(percentageValue - animatePercentage) > 0.1) {
            animatePercentage += (percentageValue - animatePercentage) / 100;
        }
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
            --percentage-width: {animatePercentage}%;
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
        width: calc(var(--percentage-width) * 0.9);
        height: inherit ;
        background-color: var(--color);
    }
    #bar::after {
        float: right;
        content: attr(value);
        /* overflow: hidden; */
    }
</style>