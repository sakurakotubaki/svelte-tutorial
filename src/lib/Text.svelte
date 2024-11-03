<script lang="ts">
    const name = "シェスタ"
    const space = "スペース"
</script>

{#if name === "シェスタ"}
  <p>I am {name}</p>
{:else if name === "スペース"}
  <p>I am {space}</p>
{:else}
  <p>I am ???</p>
{/if}