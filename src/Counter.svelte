<script>
  let count = 0;

  function increment() {
    count += 1;
  }

  function decrement() {
    count -= 1;
  }
</script>

<style>
  button {
    padding: 10px 20px;
    font-size: 16px;
    margin: 5px;
  }

  h2 {
    color: #4CAF50;
  }
</style>

<h2>Counter: {count}</h2>
<button on:click={increment}>Increase</button>
<button on:click={decrement}>Decrease</button>
