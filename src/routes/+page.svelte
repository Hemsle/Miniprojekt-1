<!--+page.svelte-->
<script>
    import Keyboard from "$lib/components/Keyboard.svelte";

    let display = $state("");
    function keyDown(e) {
        console.log(e.target.value);

        let val = e.target.value; // Knappens value-värde
        if (val === "ac") {
            memClear();
        } else if (Number(val) >= 0 && Number(val) < 10) {
            addDigit(val);
        } else if (val == "+" || val == "-" || val == "/" || val == "*") {
            setOperator(val);
        } else if (val == ",") {
            addComma();
        } else {
            calculate()
        }
    }

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
        display += digit;

        console.log(display);
    }

    /**
     * Lägger till decimaltecken
     */
    function addComma() {
        if (!isComma) {
            //hindrar dubbla komman
            display += ".";
            isComma = true;
        }
    }

    function setOperator(operator) {
        arithmetic = operator;
        if (!isNaN(parseFloat(display))) {
            memory = parseFloat(display);
        }
        clear();
    }

    function calculate() {
        if(display === ""){
            return;//om inget är skrivet
        }

        let current = parseFloat(display);
        let result;

        switch (arithmetic) {
            case "+":
                result = memory + current;
                break;
            case "-":
                result = memory - current;
                break;
            case "/":
                if (current === 0) {
                    /** hindrar division med noll att bli infinity */
                    result = "undefined";
                    isResult = true;
                } else {
                    result = memory / current;
                }
                break;
            case "*":
                result = memory * current;
                break;
            case null:
                result = current;
                break;
        }

        arithmetic = null;
        if (display === "") {
            display = memory;
            isResult = true; /** lagrar att det finns ett resultat */
        } else {
            display = result;
            isResult = true;
        }
    }

    function clear() {
        display = "";
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
    <legend>KeyBoard</legend>
    <input type="text" value={display} disabled/>
</main>

<Keyboard {keyDown}></Keyboard>

