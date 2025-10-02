<script>
    export let addDigit;
    export let addComma;
    export let setOperator;
    export let calculate;
    export let clear;
</script>

<section id="keyBoard">
    <button on:click={() => addDigit("7")}>7</button>
    <button on:click={() => addDigit("8")}>8</button>
    <button on:click={() => addDigit("9")}>9</button>
    <button class="action" on:click={() => setOperator("+")}>+</button>

    <button on:click={() => addDigit("4")}>4</button>
    <button on:click={() => addDigit("5")}>5</button>
    <button on:click={() => addDigit("6")}>6</button>
    <button class="action" on:click={() => setOperator("-")}>-</button>

    <button on:click={() => addDigit("1")}>1</button>
    <button on:click={() => addDigit("2")}>2</button>
    <button on:click={() => addDigit("3")}>3</button>
    <button class="action" on:click={() => setOperator("x")}>x</button>

    <button class="action" on:click={() => addComma()}>,</button>
    <button on:click={() => addDigit("0")}>0</button>
    <button on:click={() => calculate()}>=</button>
    <button class="action" on:click={() => setOperator("/")}>/</button>

    <button id="clear" style="grid-column: span 4;" on:click={() => clear}
        >CLEAR</button
    >
</section>

<style lang="scss">
    #keyBoard {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 1px;
        padding: 10px;
    }

    button {
        height: 80px;
        border-radius: 5px;
        font-size: 40px;
        color: black;
        background-color: rgb(224, 224, 224);
        cursor: pointer;

        &:hover {
            background-color: rgb(198, 198, 198);
        }
    }

    .action {
        color: rgb(72, 209, 255);
    }

    #clear {
        width: 100%;
    }
</style>
