<script lang="ts">
  // 基本的な人物の型
  interface Person {
    name: string;
    age: number;
  }

  // 兄弟の型（Personを拡張）
  interface Sibling extends Person {
    birthOrder?: number;  // 任意の出生順
    isEldest?: boolean;   // 長子かどうか
  }

  // 型付きのプロパティ
  let siblings: Sibling[] = [
    { name: "太郎", age: 30, birthOrder: 1, isEldest: true }, 
    { name: "次郎", age: 28, birthOrder: 2 }, 
    { name: "三郎", age: 20, birthOrder: 3 }
  ];

  // 型付きの関数
  function addSibling(newSibling: Sibling): void {
    siblings = [...siblings, newSibling];
  }

  function removeSibling(name: string): void {
    siblings = siblings.filter(sib => sib.name !== name);
  }

  function getSiblingByAge(age: number): Sibling | undefined {
    return siblings.find(sib => sib.age === age);
  }

  // 計算プロパティ
  $: averageAge = siblings.reduce((sum, sib) => sum + sib.age, 0) / siblings.length;
  $: eldestSibling = siblings.find(sib => sib.isEldest);
</script>

<div class="siblings-container">
  <h2>兄弟リスト</h2>
  
  <ul>
    {#each siblings as sibling (sibling.name)}
      <li class="sibling-item" class:eldest={sibling.isEldest}>
        <span class="name">{sibling.name}</span>
        <span class="age">{sibling.age}歳</span>
        {#if sibling.birthOrder}
          <span class="order">（第{sibling.birthOrder}子）</span>
        {/if}
        <button 
          class="remove-button"
          on:click={() => removeSibling(sibling.name)}
        >
          削除
        </button>
      </li>
    {/each}
  </ul>

  <div class="stats">
    <p>平均年齢: {averageAge.toFixed(1)}歳</p>
    {#if eldestSibling}
      <p>長子: {eldestSibling.name}</p>
    {/if}
  </div>
</div>

<style>
  .siblings-container {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
  }

  .sibling-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 12px;
    margin: 8px 0;
    background-color: #f5f5f5;
    border-radius: 6px;
  }

  .eldest {
    background-color: #e3f2fd;
    border-left: 4px solid #2196f3;
  }

  .name {
    font-weight: bold;
    min-width: 80px;
  }

  .age {
    color: #666;
  }

  .order {
    color: #888;
    font-size: 0.9em;
  }

  .remove-button {
    margin-left: auto;
    padding: 4px 8px;
    background-color: #ff5252;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  .remove-button:hover {
    background-color: #ff1744;
  }

  .stats {
    margin-top: 20px;
    padding: 16px;
    background-color: #fff3e0;
    border-radius: 6px;
  }

  .stats p {
    margin: 8px 0;
    color: #455a64;
  }
</style>