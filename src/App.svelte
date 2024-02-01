<script lang="ts">
  import Counter from './lib/Counter.svelte';

  let id = 1;
  let data = [{id: 0, value: 0, title: 'new'}];

  let titleList = '';
  let sum = 0;

  function increment(id) {
    data = data.map(item => {
      if (item.id === id) {
        return {...item, value: ++item.value}
      }
      return item;
    });

    update();
  }

  function decrement(id) {
    data = data.map(item => {
      if (item.id === id && item.value > 0) {
        return {...item, value: --item.value};
      }
      return item;
    })

    update();
  }

  function refresh(id) {
    data = data.map(item => {
      if (item.id === id) {
        return {...item, value: 0};
      }
      return item;
    })

    update();
  }

  function cancel(id) {
    data = data.filter(item => item.id !== id);

    update();
  }

  function changeTitle(event) {
    update();
  }

  function newCounter() {
    data = [...data, {id: id++, value: 0, title: 'new'}];

    update();
  }

  function update() {
    let temp = 0;
    let tempTitle = '';
    data.map(item => {
      temp += item.value;
      tempTitle += `${item.title}, `;
      console.log(tempTitle);
    });
    titleList = tempTitle;
    sum = temp;
  }
</script>

<header>
  <h1 class="text-6xl">Multiple Counter</h1>
</header>
<main class="app-main">
  <div class="container">
    {#each data as item (item)}
      <Counter value={item} increment={increment} decrement={decrement} refresh={refresh} cancel={cancel} changeTitle={changeTitle}/>
    {/each}
    <div class="new-counter" on:click={newCounter}>new counter</div>
    <p>title list: {titleList}</p>
    <p>sum of count: {sum}</p>
  </div>
</main>
<footer class="app-footer">
</footer>

<style lang="scss">
  .container {
    max-width: 54rem;
    margin: 0 auto;
    padding: 0 1rem;
    position: relative;
  }

  .text-6xl {
    font-size: 4rem;
    font-weight: inherit;
  }

  .new-counter {
    background-color: rgb(104,211,145);
    border-radius: 0.25rem;
    cursor: pointer;
    margin: auto;
    max-width: 24rem;
    text-align: center;
    color: #fff;
  }
</style>
