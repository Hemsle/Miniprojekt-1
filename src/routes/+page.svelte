<script>
    import Display from "$lib/components/Display.svelte";
    import Keyboard from "$lib/components/Keyboard.svelte";

    let value = ""; // displayen

    let memory = 0; // Lagrat/gamlat värdet från display
    let arithmetic = null; // Vilken beräkning som skall göras +,-, x eller /
    let isComma = false; //lagrar ifall det kommer finnas kommatecken
    let isResult = false; //lagrar ifall det finns ett resultat

    function addDigit(digit) {
        /**
         * när man vill påbörja en ny uträkning rensas displayen
         */
        if (isResult) {
            clear();
            isResult = false;
        }
        value += digit;
    }

    /**
     * Lägger till decimaltecken
     */
    function addComma() {
        if (!isComma) {
            //hindrar dubbla komman
            value += ".";
            isComma = true;
        }
    }

    function setOperator(operator) {
        arithmetic = operator;
        if (!isNaN(parseFloat(value))) {
            memory = parseFloat(value);
        }
        clear();
    }

    function calculate() {
        let result;
        console.log(arithmetic);

        switch (arithmetic) {
            case "+":
                result = memory + value;
                break;
            case "-":
                result = memory - value;
                break;
            case "/":
                if (value === "0") {
                    /** hindrar division med noll att bli infinity */
                    value = "undefined";
                } else {
                    result = memory / value;
                }
                break;
            case "*":
                result = memory * value;
                break;
            case null:
                result = value;
                break;
        }

        arithmetic = null;
        if (value === "") {
            value = memory;
            isResult = true; /** lagrar att det finns ett resultat */
            console.log(memory + " " + isResult);
        } else {
            value = result;
            isResult = true;
            console.log(result + " " + isResult);
        }
    }

    function clear() {
        value = "";
        isComma = false;
    }

    /** Rensar allt, reset */
    function memClear() {
        memory = 0;
        arithmetic = null;
        clear();
    }


</script>

<svelte:head>
    <title>Kalkylator</title>
</svelte:head>

<main>
    <!-- Display får value -->
    <Display {value} />

    <!-- Keyboard får alla funktioner -->
    <Keyboard 
        {addDigit} 
        {addComma} 
        {setOperator} 
        {calculate} 
        {clear} 
    />
</main>