<script lang="ts">
  let count:number = $state(0)

  function increment() {
    count += 1
  }

</script>

<h1>{count} {count === 5 ? "５回クリック": "click me"}</h1>
<button on:click={increment}>count up</button>

<style>
  h1 {
    color: blue;
  }
</style>