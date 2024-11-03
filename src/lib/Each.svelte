<script>
    const siblings = [
      { name: "太郎", age: 30 }, 
      { name: "次郎", age: 28 }, 
      { name: "三郎", age: 20 }
    ]
    </script>
    
    <ul>
      {#each siblings as sibling, i}
        <li>{sibling.name}: {sibling.age}歳</li>
      {/each}
    </ul>