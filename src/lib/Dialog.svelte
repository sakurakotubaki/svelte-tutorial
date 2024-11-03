<script lang="ts">
    function dialog(): void {
        alert("スカッシュマージするよ")
    }
</script>

<h1 class="text-orange-500">Dialog</h1>
<button on:click={() => {dialog()}}>click mi</button>

<style>
    button {
        background-color: gold;
    }
</style>