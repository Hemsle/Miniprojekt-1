<!--Keyboard.svelte-->
<script>
    let { keyDown } = $props();
</script>

<main>
    <section id="keyBoard">
        <button onclick={keyDown} value="7">7</button>
        <button onclick={keyDown} value="8">8</button>
        <button onclick={keyDown} value="9">9</button>
        <button class="action" onclick={keyDown} value="+">+</button>

        <button onclick={keyDown} value="4">4</button>
        <button onclick={keyDown} value="5">5</button>
        <button onclick={keyDown} value="6">6</button>
        <button class="action" onclick={keyDown} value="-">-</button>

        <button onclick={keyDown} value="1">1</button>
        <button onclick={keyDown} value="2">2</button>
        <button onclick={keyDown} value="3">3</button>
        <button class="action" onclick={keyDown} value="*">x</button>

        <button class="action" onclick={keyDown} value=",">,</button>
        <button onclick={keyDown} value="0">0</button>
        <button onclick={keyDown} value="=">=</button>
        <button class="action" onclick={keyDown} value="/">/</button>

        <button
            id="clear"
            style="grid-column: span 4;"
            onclick={keyDown}
            value="ac">CLEAR</button
        >
    </section>
</main>

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
