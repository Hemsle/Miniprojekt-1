<svelte:head>
    <title>Kalkylator</title>
</svelte:head>

<main>
    <input type="text" id="lcd" disabled="disabled" />
    <section id="keyBoard">
        <button id="b7">7</button>
        <button id="b8">8</button>
        <button id="b9">9</button>
        <button class="action" id="add">+</button>

        <button id="b4">4</button>
        <button id="b5">5</button>
        <button id="b6">6</button>
        <button class="action" id="sub">-</button>

        <button id="b1">1</button>
        <button id="b2">2</button>
        <button id="b3">3</button>
        <button class="action" id="mul">x</button>

        <button id="comma">,</button>
        <button id="b0">0</button>
        <button id="enter">=</button>
        <button class="action" id="div">/</button>

        <button id="clear" style="grid-column: span 4;">CLEAR</button>
    </section>
</main>
