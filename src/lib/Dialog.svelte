<script lang="ts">
    function dialog(): void {
        alert("click me")
    }
</script>

<button on:click={() => {dialog()}}>click mi</button>