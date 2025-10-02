<script>
    export let value = ""; // får värdet från parent
</script>

<input type="text" value={value} disabled />
 
<style lang="scss">
    input {
        width: 100%;
        font-size: 3.5rem;
        margin-bottom: 10px;
        color: green;
        background-color: black;
        text-align: right;
        padding: 10px 4px 10px 4px;
        font-family: arial;
        border: 1px solid yellow;
        border-radius: 4px;
    }
</style>